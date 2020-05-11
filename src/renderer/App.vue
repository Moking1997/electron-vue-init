<template>
  <div id="app">
    <el-menu
      :default-active="$route.path"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
      background-color="#545c64"
      text-color="#fff"
      :router="true"
      active-text-color="#ffd04b"
    >
      <el-menu-item index="/main">主页</el-menu-item>
      <el-menu-item index="/parse">分页 1</el-menu-item>
      <el-menu-item index="/help">分页 2</el-menu-item>
    </el-menu>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "site-control",
  data() {
    return {
      activeIndex: "1"
    };
  },
  methods: {
    handleSelect(key, keyPath) {}
  }
};
</script>

<style>
html * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
