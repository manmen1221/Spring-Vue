<template>
  <el-container>
    <el-dialog title="注 册" :visible.sync="注册窗口显示" destroy-on-close :close-on-click-modal="false">
      <el-form :model="sign" ref="sign" :rules="rules" status-icon>
        <el-form-item prop="us">
          <el-input v-model="sign.us" placeholder="请输入账号"></el-input>
        </el-form-item>
        <el-form-item prop="ps">
          <el-input v-model="sign.ps" placeholder="请输入密码" type="password"></el-input>
        </el-form-item>
        <el-form-item prop="ps2">
          <el-input v-model="sign.ps2" placeholder="请重复密码" type="password"></el-input>
        </el-form-item>
        <el-button type="primary" @click="submitSignForm('sign')">注册</el-button>
      </el-form>
    </el-dialog>
    <el-main>
      <el-container>
        <img src="../assets/login.png" width="70%" htight="100%">
        <el-aside width="30%">
          <el-header/>
          <img src="../assets/login.png" width="100%" height="10%">
          <el-form :model="user" ref="user" :rules="rules" status-icon>
            <el-form-item prop="us">
              <el-input v-model="user.us" placeholder="请输入账号"></el-input>
            </el-form-item>
            <el-form-item prop="ps">
              <el-input v-model="user.ps" placeholder="请输入密码" type="password"></el-input>
            </el-form-item>
            <el-button type="primary" @click="submitLoginForm('user')">登录</el-button>
            <el-button @click="显示注册窗口()">注册</el-button>
          </el-form>
        </el-aside>
      </el-container>
    </el-main>
  </el-container>
</template>

<script>
export default {
  name: 'Login',
  data () {
    var checkPs = (rule, value, callback) => {
      if (value === '' || value === null) {
        callback(new Error('请再次输入密码'))
      } else if (value !== this.sign.ps) {
        callback(new Error('两次输入密码不一致!'))
      } else {
        callback()
      }
    }
    return {
      注册窗口显示: false,
      user: {us: null, ps: null},
      sign: {us: null, ps: null, ps2: null},
      rules: {
        us: [{required: true, message: '请输入账号', trigger: 'blur'}, {min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur'}],
        ps: [{required: true, message: '请输入密码', trigger: 'blur'}, {min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur'}],
        ps2: [{validator: checkPs, trigger: 'blur'}, {min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur'}]
      }
    }
  },
  methods: {
    submitLoginForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.请求登录()
        } else {
          return false
        }
      })
    },
    submitSignForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.请求注册()
        } else {
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    },
    显示注册窗口 () {
      this.注册窗口显示 = true
      this.resetForm('sign')
    },
    请求登录 () {
      this.$axios.post('/Login', {us: this.user.us, ps: this.$md5(this.user.ps)}).then(res => {
        if (res.data.错误) {
          alert(res.data.警告)
          this.user.ps = null
        } else {
          this.$router.push({
            name: 'Market',
            params: {
              us: res.data.用户,
              qx: res.data.权限,
              lg: true
            }
          })
        }
      }).catch(fail => {
        alert('网络错误')
      })
    },
    请求注册 () {
      this.$axios.post('/Sign', {us: this.sign.us, ps: this.$md5(this.sign.ps)}).then(res => {
        alert(res.data.信息)
        this.注册窗口显示 = false
      }).catch(fail => {
        alert('网络错误')
      })
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .white-space {
    white-space:pre
  }
</style>
