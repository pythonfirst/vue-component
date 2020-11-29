<template>
  <div>
    <ZInput
      :value="value"
      :placeholder="placeholder"
      @input="handleInput"
      @change="handleChange"
      @blur="handleBlur"
    >
      <i class="iconfont" slot="icon">&#xe62a;</i>
      <Suggestion
        slot="append"
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
      value: ""
    };
  },
  created() {
    this.placeholder =
      this.suggestions.length !== 0 ? this.suggestions[0] : "请输入";
  },
  methods: {
    /**
     * 触发的回调事件
     */
    handleSelect(value) {
      console.log("======触发了select回调事件======", value);
      this.value = value;
      this.$emit("select", value);
    },
    handleInput(value) {
      console.log("======触发了input事件======", value);
      this.value = value;
      this.$emit("input", value);
    },
    handleChange() {
      console.log("======触发了change事件======", this.value);
      this.$emit("change", this.value);
    },
    handleBlur() {
      console.log("======触发了blur事件======", this.value);
      this.$emit("blur", this.value);
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
