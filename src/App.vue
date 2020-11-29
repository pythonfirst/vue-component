<template>
  <div id="app">
    <div class="position">占位</div>
    <Search :suggestions="suggestions"></Search>
  </div>
</template>
<script>
import Search from "./components/Search";
export default {
  components: { Search },
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
  }
};
</script>
<style scoped>
.position {
  width: 100%;
  height: 500px;
}
</style>
