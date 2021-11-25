<template>
  <el-container style="height: 100%; border: 1px solid #eee">
    <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
      <el-menu :default-openeds="['1']">
        <el-submenu index="1">
          <template slot="title">Dashboard</template>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title">房价分析</template>
          <el-menu-item index="2-1">选项1</el-menu-item>
          <el-menu-item index="2-2">选项2</el-menu-item>
          <el-menu-item index="2-3">选项3</el-menu-item>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title">房价查询</template>
        </el-submenu>
        <el-submenu index="4">
          <template slot="title">购房评估</template>
        </el-submenu>
      </el-menu>
    </el-aside>
  </el-container>
</template>

<script>
export default {
  name: "Main",
};
</script>

<style scoped>
.container {
  height: 100%;
  width: 100%;
}

.el-header {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
</style>
