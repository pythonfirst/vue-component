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
  font-family: Helvetica Neue, Helvetica, PingFang SC, Hiragino Sans GB,
    Microsoft YaHei, SimSun, sans-serif;
}
.container {
  width: 200px;
}
.input {
  /* -webkit-appearance: none; */
  background-color: #fff;
  background-image: none;
  border-radius: 4px;
  border: 1px solid #dcdfe6;
  box-sizing: border-box;
  color: #606266;
  display: inline-block;
  font-size: inherit;
  height: 40px;
  line-height: 40px;
  outline: none;
  padding: 0 15px;
  width: 100%;
  cursor: pointer;
}
.input::placeholder {
  color: rgb(191, 195, 202);
}
.input:focus {
  outline: none;
  border-color: #409eff;
}
</style>
