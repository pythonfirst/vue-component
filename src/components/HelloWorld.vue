<template>
  <div class="hello">
    <i-button
      ref="button"
      size="large"
      :disabled="false"
      type="hello"
      style="backgroundColor: blue;"
      class="hello"
      @on-click="handleClick"
    >
      button
      <p slot="icon">h</p>
    </i-button>
  </div>
</template>

<script>
/**
 * 通过type="hello" 测试button组件的
 * inheritattrs:false 及
 * $attrs api
 */
import Button from "./Button";
export default {
  name: "HelloWorld",
  components: { "i-button": Button },
  props: {
    msg: String
  },
  methods: {
    handleClick(e) {
      console.log(this.$refs.button.size); // 通过$refs获取Button组件及其数据
      console.log("e", e);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less"></style>
