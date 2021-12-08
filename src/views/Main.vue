<template>
  <!-- <el-container>
    <el-aside width="260px">Aside</el-aside>
    <el-container>
      <el-header>Header</el-header>
      <el-main>Main</el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </el-container> -->

  <el-container>
    <el-header class="main-header" style="height:70px;">
      <nav class="navbar navbar-static-top">
        <!-- Logo -->
        <a href="index.html" class="logo" style="text-align:center"></a>
        <a href="#" class="sidebar-toggle">
          <i aria-hidden="true" :class="isCollapse?'fa fa-indent':'fa fa-outdent'"></i>
        </a>
        <div class="nav-search">
          <el-input placeholder="请输入内容" size="small" prefix-icon="el-icon-search"></el-input>
        </div>

      </nav>
    </el-header>
    <el-container>
      <el-aside :width="tabWidth+'px'">
        <el-menu default-active="5-1" class="el-menu-vertical-demo" background-color="#108ee9">
          <sidebar-item v-for="menu in menuList" :key="menu.path" :item="menu" />
        </el-menu>
      </el-aside>
      <el-container>
        <iframe name="right" id="iframepage" class="el-main" src="questionBasicList.html" width="100%" height="100%" frameborder="0" ranat="server"></iframe>
      </el-container>
    </el-container>
  </el-container>
</template>

<script>

</script>

<style scoped>
/* .el-container{
  height: 100%;
}

.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 600px;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
} */
</style>
