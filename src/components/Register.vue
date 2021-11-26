<template>
  <el-form ref="form" :model="form" label-width="80px" class="register-box" :rules="rules">
    <h2 class="login-title">注册用户</h2>
    <el-form-item label="用户名" prop="account" for='account'>
      <el-input id='account' placeholder="2~12个字符(仅限字母、数字与下划线)" v-model="form.account"></el-input>
    </el-form-item>
    <el-form-item label="邮箱(选填)" prop="email" for='email'>
      <el-input id='email' v-model="form.email"></el-input>
    </el-form-item>
    <el-form-item label="地区" prop="region" for='region'>
      <el-select id='region' v-model="form.region" clearable placeholder="请选择你的地区" style="float: left; width:150px;">
        <el-option v-for="item in form.options" :key="item.value" :label="item.label" :value="item.value"></el-option>
      </el-select>
    </el-form-item>
    <el-form-item label="密码" prop="password" for='password'>
      <el-input id='password' type='password' placeholder="8~16个字符(必须包含字母及数字)" v-model="form.password"></el-input>
    </el-form-item>
    <el-form-item label="确认密码" prop="ackPassword" for='ackPassword'>
      <el-input id='ackPassword' type='password' v-model="form.ackPassword"></el-input>
    </el-form-item>
    <span class='tip'>已有账号？<router-link to='/login' class="link">去登录！</router-link></span><br>
    <el-form-item>
      <el-button type="primary" round @click="register('form')" style="margin: 0 30px 0 0px; padding: 16px 53px;">注册</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  name: 'Register',
  data() {
    var validatePassword = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('请再次输入密码'));
      } else if (value !== this.form.password) {
        callback(new Error('两次输入密码不一致!'));
      } else {
        callback();
      }
    };
    return {
      form: {
        account: '',
        email: '',
        password: '',
        ackPassword: '',
        region: '',
        options: [{
          value: '选项1',
          label: '鼓楼区'
        }, {
          value: '选项2',
          label: '台江区'
        }, {
          value: '选项3',
          label: '晋安区'
        }, {
          value: '选项4',
          label: '马尾区'
        }, {
          value: '选项5',
          label: '仓山区'
        }, {
          value: '选项6',
          label: '闽侯县'
        }, {
          value: '选项7',
          label: '连江县'
        }, {
          value: '选项8',
          label: '平潭县'
        }, {
          value: '选项9',
          label: '福清市'
        }, {
          value: '选项10',
          label: '长乐区'
        }]
      },
      rules: {
        account: [
          { required: true, message: '必填项', trigger: 'change' }
        ],
        email: [
          { type: 'email', message: '请输入正确的邮箱地址', trigger: 'change' }
        ],
        region: [
          { required: true, message: '必填项', trigger: 'change' }
        ],
        password: [
          { required: true, message: '必填项', trigger: 'change' },
          { min: 8, max: 16, message: '密码长度 8~16 个字符', trigger: 'blur' }
        ],
        ackPassword: [
          { required: true, message: '请再次输入密码', trigger: 'change' },
          { validator: validatePassword, trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    register(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$message.success('注册成功！');
          this.$router.push('/login');
        } else {
          this.$message.error('请填写必填项！');
          return false;
        }
      });
    }
  },
  // watch的应用: 同名、immediate、deep、handler(newVal,oldVal)、属性监控==>字符串形式!
  watch: {
    // 若直接监听 form 对象 + deep:true 属性 ==> 一旦form对象内的任何属性改变都会触发监听器内的 handler() ==> 性能开销较大!
    // 优化: "字符串形式监听" ==> 不需要deep属性 + `'form.属性':{}` 
    // 现在是只监听 form 对象的 ackPassword 属性!
    'form.ackPassword': {
      handler(newVal, oldVal) {
        if (newVal == this.form.password) {
          console.log('Coincidence!');
        }
      },
      immediate: true,
      // deep: true
    }
  }

}
</script>

<style scoped>
.register-box {
  width: 385px;
  border: 1px solid #dcdfe6;
  padding: 30px 45px 10px 0px;
  border-radius: 5px;
  box-shadow: 0 0 30px #dcdfe6;
  position: absolute;
  top: 19%;
  left: 37%;
}

.login-title {
  text-align: center;
  padding: 0 0 15px 30px;
}

.tip {
  color: white;
  position: relative;
  left: 30px;
  bottom: 10px;
}

.link:hover {
  color: red;
}
</style>