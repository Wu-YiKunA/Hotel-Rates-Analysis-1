<template>
  <div style="width:100%; height:100%" class='container'>
    <h1 class='logo'>福州房价查询网</h1>
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
          account: [
            { required: true, message: '请输入用户名', trigger:'change'}
          ],
          password: [
            { required: true, message: '请输入密码', trigger: 'change' },
            { min: 6, max: 16, message: '密码长度在 6 到 16 个字符', trigger: 'blur' }
          ]
        }
    };
  },
  methods: {
    login(formName) {``
      this.$refs[formName].validate((valid) => {
        if (valid) {
          // 管理员
          if(this.form.account === "admin" && this.form.password === "123456") {
            this.$message.success('成功登录后台管理系统~')
            this.$router.push('/admin/main')
          }
          // 客户 
          else if(this.form.account === "user" && this.form.password === "123456") {
            this.$message.success('成功登录福州房价查询系统~')
            this.$router.push('/user/main')
          } else {
            this.$message.error('用户名或密码错误..');
          }
        } else {
          this.$message.error('请检查你的账号/密码格式是否正确..');
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
.container {
  background-image: url("http://ww1.sinaimg.cn/large/006V2BYXly1gwr4x6wbv8j31hc0hswqw.jpg");
  background-repeat: round;
}

.logo{
  float: left;
  padding-left: 50px;
  margin: 25px;
  background-image: url('http://gdown.baidu.com/img/0/512_512/7d22ac20ac5fa4015074fa5b7e46b258.png');
  background-size: 40px;
  background-position: left;
  background-repeat: no-repeat;
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