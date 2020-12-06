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
import Vue from "vue";
import Child from "./Child";
import Button from "../Button";
export default {
  name: "Parent",
  components: { Child, Button },
  provide() {
    // 注意state为reactivity，只传message不管用
    this.state = Vue.observable({
      message: 200
    });
    return {
      message: this.message,
      app: this,
      state: this.state
    };
  },
  data() {
    return {
      message: "100",
      state: null
    };
  },
  methods: {
    changeMessage() {
      this.message = Math.floor(Math.random() * 100);
      this.state.message = Math.floor(Math.random() * 100);
    }
  }
};
</script>

<style></style>
