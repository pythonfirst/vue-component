<template>
  <div class="home">
    <Input />
  </div>
</template>

<script>
import Input from "../components/Input";
export default {
  name: "Home",
  components: {
    Input
  },
  provide() {
    return {
      foo: "foo"
    };
  },
  data() {
    return {
      suggestions: [
        {
          text: "北京"
        }
      ]
    };
  }
};
</script>
