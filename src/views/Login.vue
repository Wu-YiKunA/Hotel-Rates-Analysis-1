<template>
    <el-form ref="form" :model="form" label-width="80px" class="login-box" :rules="rules">
      <h2 class="login-title">欢迎登录</h2>
      <el-form-item label="账号" prop="account" for='account'>
        <el-input id='account' placeholder="请输入用户名" v-model="form.account"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password" for='password'>
        <el-input id='password' type='password' placeholder="请输入密码" v-model="form.password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" round @click="login('form')"  style="margin: 0 30px 0 -20px;">登录</el-button>
        <!-- router-link: 无需再写 method 跳转 -->
        <router-link to='/register' class="el-button el-button--danger is-round">注册</router-link>
        <!-- 等价于 <el-button type="danger" round >注册</el-button> -->
      </el-form-item>
    </el-form>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      form: {
        account: "",
        password: "",
      }
    };
  },
  methods: {
    login(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          // 管理员
          if(this.form.account === "admin" && this.form.password === "12345678") {
            this.$message.success('成功登录福州房价查询系统, 欢迎你, Admin ~')
            this.$router.push('/main')
          }
          // 客户
          else if(this.form.account === "user" && this.form.password === "12345678") {
            this.$message.success('成功登录福州房价查询系统, 欢迎你, User ~')
            this.$router.push('/user/main')
          } else {
            this.$message.error('用户名或密码错误..');
          }
        } else {
          this.$message.error('请检查你的账号/密码格式是否正确..');
          return false;
        }
      });
    }
  },
};
</script>

<style scoped>
.login-box {
  width: 350px;
  border: 1px solid #dcdfe6;
  padding: 30px 45px 10px 0px;
  border-radius: 5px;
  box-shadow: 0 0 30px #dcdfe6;
  position: absolute;
  top: 35%;
  left: 37%;
}

.login-title {
  text-align: center;
  padding: 0 0 15px 30px;
}
</style>
