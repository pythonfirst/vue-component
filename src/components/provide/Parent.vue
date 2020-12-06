<template>
  <div>
    <div>
      Parent message: {{ message }}
      <Button @click.native="changeMessage">change message</Button>
    </div>

    <Child></Child>
    <div class="todo">
      TODO: Patent provide 通过函数形式可以使用this;
      通过对象形式无法通过this使用data里的变量
    </div>
  </div>
</template>

<script>
import Child from "./Child";
import Button from "../Button";
export default {
  name: "Parent",
  components: { Child, Button },
  provide() {
    return {
      message: this.message,
      app: this
    };
  },
  data() {
    return {
      message: "100"
    };
  },
  methods: {
    changeMessage() {
      this.message = Math.floor(Math.random() * 100);
    }
  }
};
</script>

<style></style>
