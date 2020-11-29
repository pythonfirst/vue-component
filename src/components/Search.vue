<template>
  <div>
    <ZInput
      :value="value"
      :placeholder="placeholder"
      @keydown.up.native.prevent="handleKeyUp"
      @keydown.down.native.prevent="handleKeyDown"
      @keydown.enter.native.prevent="handleEnter"
      @input="handleInput"
      @change="handleChange"
      @blur="handleBlur"
    >
      <i @click="submit" class="iconfont" slot="icon">&#xe62a;</i>
      <Suggestion
        slot="append"
        :index="index"
        :data="suggestions"
        @select="handleSelect"
      ></Suggestion>
    </ZInput>
  </div>
</template>

<script>
import ZInput from "./Input";
import Suggestion from "./Suggestion";
export default {
  components: {
    ZInput,
    Suggestion
  },
  props: {
    suggestions: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      placeholder: "",
      value: "",
      index: null
    };
  },
  created() {
    this.placeholder =
      this.suggestions.length !== 0 ? this.suggestions[0] : "请输入";
  },
  methods: {
    handleKeyUp() {
      console.log("keyup event", this.index);
      this.index = this.index > 0 ? this.index - 1 : this.index;
      this.value = this.suggestions[this.index];
    },
    handleKeyDown() {
      console.log("keydown event", this.index);
      this.index =
        this.index < this.suggestions.length - 1 ? this.index + 1 : this.index;
      this.value = this.suggestions[this.index];
    },
    handleEnter() {
      console.log("enter event", this.index);
      if (this.$children[0].focused && this.index) {
        this.$children[0].focused = false;
        this.value = this.suggestions[this.index];
      }
      this.submit();
      this.$emit("enter", this.value);
    },
    handleSelect(e) {
      console.log("======触发了select回调事件======", e);
      this.value = e.value;
      this.index = e.index;
      // this.submit();
      this.$emit("select", e.value);
    },
    handleInput(value) {
      console.log("======触发了input事件======", value);
      this.value = value;
      this.index = null;
      this.$emit("input", value);
    },
    handleChange() {
      console.log("======触发了change事件======", this.value);
      this.$emit("change", this.value);
    },
    handleBlur(e) {
      console.log("======触发了blur事件======", this.value);
      this.$emit("blur", this.value, e);
    },
    submit() {
      console.log("======触发提交事件======");
      this.$children[0].focused = false;
      this.$emit("submit", this.value);
    }
  }
};
</script>

<style>
@font-face {
  font-family: "iconfont"; /* project id 1152678 */
  src: url("//at.alicdn.com/t/font_1152678_y3ayb6d4z8.eot");
  src: url("//at.alicdn.com/t/font_1152678_y3ayb6d4z8.eot?#iefix")
      format("embedded-opentype"),
    url("//at.alicdn.com/t/font_1152678_y3ayb6d4z8.woff2") format("woff2"),
    url("//at.alicdn.com/t/font_1152678_y3ayb6d4z8.woff") format("woff"),
    url("//at.alicdn.com/t/font_1152678_y3ayb6d4z8.ttf") format("truetype"),
    url("//at.alicdn.com/t/font_1152678_y3ayb6d4z8.svg#iconfont") format("svg");
}
.iconfont {
  cursor: pointer;
  position: absolute;
  right: -5px;
  top: 50%;
  color: rgb(77, 79, 83);
  transform: translate(-50%, -50%);
  margin: auto;
  font-family: "iconfont" !important;
  font-size: 22px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -webkit-text-stroke-width: 0.2px;
  -moz-osx-font-smoothing: grayscale;
}
.iconfont:hover {
  color: rgb(77, 165, 255);
}
</style>
