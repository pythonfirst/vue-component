<template>
  <div>
    <ZInput :value="value" :placeholder="placeholder" @input="handleInput">
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
      console.log("======触发了回调事件======");
      this.value = value;
    },
    handleInput(value) {
      this.value = value;
    }
  }
};
</script>

<style></style>
