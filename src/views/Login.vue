<template>
  <div style="width:100%; height:100%">
    <h1 class='logo'>福州房价分析网</h1>
    <el-form ref="form" :model="form" label-width="80px" class="login-box" :rules="rules">
      <h2 class="login-title">欢迎登录</h2>
      <el-form-item label="账号" prop="account" class="account">
        <el-input placeholder="请输入用户名" v-model="form.account" class="input"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password" class="password">
        <el-input type='password' placeholder="请输入密码" v-model="form.password" class="input"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" round @click="login('form')"  style="margin: 0 30px 0 -20px;">登录</el-button>
        <el-button type="danger" round @click="register">注册</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      form: {
        account: "",
        password: "",
      },
      rules: {
          password: [
            { min: 6, max: 16, message: '密码长度在 6 到 16 个字符', trigger: 'blur' }
          ]
        }
    };
  },
  methods: {
    login(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$router.push('/main')
        } else {
          this.$message.error('用户名或密码错误..');
          return false;
        }
      });
    },
    register() {
      console.log("注册");
    },
  },
};
</script>

<style scoped>
.logo{
  float: left;
  padding-left: 50px;
  margin: 25px;
  background-image: url('http://gdown.baidu.com/img/0/512_512/7d22ac20ac5fa4015074fa5b7e46b258.png');
  background-size: 40px;
  background-position: left;
  background-repeat: no-repeat;
}

.FuZhou > img{
  position: absolute;
  top: 20px;
  left: 15px;
}

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