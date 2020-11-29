<template>
  <div class="suggestion">
    <ul class="suggestion-list">
      <li
        v-for="(item, index) in data"
        :key="item"
        :class="{ highlighted: selectedIndex === index }"
        @mousedown="handleSelect(item, index)"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Suggestion",
  props: {
    data: {
      type: Array,
      default: () => []
    },
    index: {
      type: Number
    }
  },
  watch: {
    index(val) {
      this.selectedIndex = val;
    }
  },
  data() {
    return {
      selectedIndex: null
    };
  },
  methods: {
    handleSelect(value, index) {
      console.log("value", value, index);
      this.selectedIndex = index;
      this.$emit("select", { value, index });
    }
  }
};
</script>

<style scoped>
.suggestion {
  max-height: 280px;
  padding: 10px 0;
  background-color: rgb(255, 255, 255);
  border: 1px solid #e4e7ed;
  border-radius: 4px;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
  overflow: scroll;
}
.suggestion-list {
  margin: 0;
  padding: 0;
}
.suggestion-list li {
  list-style: none;
  padding: 0 20px;
  margin: 0;
  line-height: 34px;
  cursor: pointer;
  color: #606266;
  font-size: 14px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.suggestion-list li.highlighted,
.suggestion-list li:hover {
  background-color: #f5f7fa;
}
.suggestion-list li.divider {
  margin-top: 6px;
  border-top: 1px solid #000;
}
.suggestion-list li.divider:last-child {
  margin-bottom: -6px;
}
</style>
