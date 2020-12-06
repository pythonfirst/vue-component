<template>
  <button
    :class="'i-button-' + size"
    :disabled="disabled"
    style="height: 30px;"
    @click="handleClick"
  >
    <slot name="icon"></slot>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "i-button",
  inheritAttrs: false,
  props: {
    size: {
      validator(value) {
        return ["small", "large", "default"].includes(value);
      }
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  created() {
    this.$on("on-click", function(msg) {
      console.log("msg", msg);
    });
  },
  methods: {
    handleClick(event) {
      // console.log("event", event, this.$parent.$options.name); // 通过this.$parent获取父组件实例及其数据
      this.$emit("on-click", event);
    }
  }
};
</script>

<style scoped>
.i-button-default {
  width: 70px;
}
.i-button-small {
  width: 50px;
}
.i-button-large {
  width: 90px;
}
</style>
