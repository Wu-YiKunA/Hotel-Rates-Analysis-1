<template>
  <div style="width: 100%; height: 100%" class="container">
    <h1 class="logo">福州房价可视化分析系统</h1>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "Index",
};
</script>

<style scoped>
.container {
  background-image: url("http://ww1.sinaimg.cn/large/006V2BYXly1gwr4x6wbv8j31hc0hswqw.jpg");
  background-repeat: round;
}

.logo {
  float: left;
  padding-left: 50px;
  margin: 25px;
  background-image: url("http://gdown.baidu.com/img/0/512_512/7d22ac20ac5fa4015074fa5b7e46b258.png");
  background-size: 40px;
  background-position: left;
  background-repeat: no-repeat;
}
</style>
