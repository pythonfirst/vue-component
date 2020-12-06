<template>
  <div>
    <div>
      Child message(ractivity-this){{ this.app.message }}
      <span class="important">通过provide component实例this可以实现响应式</span>
    </div>
    <div>
      Child message(ractivity-observable.state.message){{ this.state.message }}
      <span class="important">通过provide component实例this可以实现响应式</span>
    </div>
    <div>Child message(no-ractivity){{ this.message }}</div>
    <Button @click.native="invokeParentMethod">invoke parent method</Button
    ><span>通过provide component实例可以调用实例的方法</span>
  </div>
</template>

<script>
import Button from "../Button";
export default {
  name: "Child",
  inject: ["message", "app", "state"],
  components: {
    Button
  },
  mounted() {
    // console.log('mounted message', this.message)
  },
  created() {
    console.log("created message", this.message, this.app.message);
  },
  methods: {
    invokeParentMethod() {
      // this.app.message = 'hello'
      this.app.changeMessage();
    }
  }
};
</script>

<style></style>
