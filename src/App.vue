<template>
  <div id="app">
    <Search :suggestions="suggestions" @submit="handleSubmit"></Search>
    <Parent></Parent>
  </div>
</template>
<script>
import Search from "./components/Search";
import Parent from "./components/provide/Parent";
export default {
  components: { Search, Parent },
  data() {
    return {
      suggestions: [
        "北京",
        "上海",
        "北京今天是个艳阳天北京今天是个艳阳天",
        "广州",
        "深圳",
        "杭州",
        "武汉",
        "成都",
        "西安",
        "重庆",
        "南京",
        "苏州",
        "青岛",
        "大连",
        "郑州"
      ]
    };
  },
  methods: {
    handleSubmit(value) {
      console.log("app submit value", value);
    }
  }
};
</script>
<style>
.todo {
  color: red;
}
.important {
  font-weight: 600;
  color: #1b7fff;
}
</style>
