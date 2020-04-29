<template>
  <div class="text-box">
    <div class="tags-list">
      <span class="tags-list-item" v-for="(item,index) in list" :key="index">
        <span class="tags-text">{{item}}</span>
        <i class="tags-text__close el-icon-close" @click="remove(index)"></i>
      </span>
      <input
        type="text"
        class="tags-input"
        v-model="text"
        v-on:keyup.13="submit"
        v-on:keyup.188="submit"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "text-to-tags",
  props: {
    list: {
      type: Array,
      default: []
    }
  },
  data() {
    return {
      text: ""
    }
  },
  methods: {
    remove(index) {
      this.list.splice(index, 1);
    },
    submit(e) {
      if (!this.text) return;
      if (this.text == ",") {
        this.text = "";
        return;
      }
      this.text = this.text.replace(",", "");
      const isNotExist = this.list.every(item => {
        return item != this.text;
      });
      if (isNotExist) {
        this.list.push(this.text.replace(",", ""));
        this.text = "";
      }
      this.$emit('change',this.list);
    }
  }
};
</script>
<style lang="scss" scoped>
.text-box {
  -webkit-appearance: none;
  background-color: #fff;
  background-image: none;
  border-radius: 4px;
  border: 1px solid #dcdfe6;
}
.tags-list-item {
  background-color: #ecf5ff;
  display: inline-block;
  height: 24px;
  padding: 0 8px;
  line-height: 22px;
  font-size: 12px;
  color: #409eff;
  border: 1px solid #d9ecff;
  border-radius: 4px;
  box-sizing: border-box;
  white-space: nowrap;
  margin: 2px 0 2px 6px;
  cursor: pointer;
}
.tags-text__close {
  background-color: #c0c4cc;
  border-radius: 50%;
  color: #909399;
}
.tags-text {
  color: #909399;
}
.tags-input {
  border: 0;
  border: none;
  outline: none;
  padding: 0;
  margin-left: 15px;
  color: #666;
  font-size: 14px;
  appearance: none;
  height: 28px;
  background-color: transparent;
}
.tags-input:focus {
  outline: none;
}
</style>