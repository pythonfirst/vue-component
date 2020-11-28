<template>
  <div class="hello">
    <i-button
      size="large"
      :disabled="false"
      type="hello"
      style="backgroundColor: blue;"
      class="hello"
    >
      button
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
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less"></style>
