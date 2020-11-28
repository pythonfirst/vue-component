<template>
  <button
    :class="'i-button-' + size"
    :disabled="disabled"
    style="backgroundColor: yellow; height: 30px;"
  >
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
    console.log(this.$attrs);
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
