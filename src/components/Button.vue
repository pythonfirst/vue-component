<template>
  <button
    :class="'i-button-' + size"
    :disabled="disabled"
    style="backgroundColor: yellow; height: 30px;"
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
  inject: ["foo"],
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
    console.log(this.$attrs, this.foo);
  },
  methods: {
    handleClick(event) {
      console.log("event", event, this.$parent.$options); // 通过this.$parent获取父组件实例及其数据
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
