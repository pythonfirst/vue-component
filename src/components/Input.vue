<template>
  <div class="container">
    <input
      ref="input"
      class="input"
      v-bind="$attrs"
      :type="type"
      :disabled="disabled"
      @input="handleInput"
      @focus="handleFocus"
      @blur="handleBlur"
      @change="handleChange"
    />
    <div class="suffix" v-show="focused">
      <slot name="append"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "Input",
  inheritAttrs: false,
  props: {
    type: {
      type: String,
      default: "text"
    },
    disabled: {
      type: Boolean,
      default: false
    },
    suggestionData: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      focused: false,
      value: ""
    };
  },
  methods: {
    focus() {
      console.log("focus...");
      this.getInput().focus();
    },
    blur() {
      this.getInput().blur();
    },
    handleBlur(event) {
      // console.log('blur...')
      this.focused = false;
      this.$emit("blur", event);
    },
    handleFocus(event) {
      // console.log('handlefocus...')
      this.focused = true;
      this.$emit("focus", event);
    },
    handleInput(event) {
      this.$emit("input", event.target.value);
    },
    handleChange(event) {
      this.$emit("change", event.target.value);
    },
    getInput() {
      return this.$refs.input;
    }
  }
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.container {
  width: 200px;
}
.input {
  width: 200px;
  cursor: pointer;
  overflow: hidden;
}
</style>
