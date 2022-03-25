<template>
  <div class="container">
    <div class="login_box">
      <div class="login_logo">
        <img src="../assets/logo.png" alt="" />
      </div>
      <el-form
    ref="LoginFormRef"
    :model="LoginFormList"
    :rules="LoginFormListRules"
  >
    <el-form-item prop="username">
      <el-input
        v-model="LoginFormList.username"
        prefix-icon="el-icon-user-solid"
        placeholder="请输入用户名"
      ></el-input>
    </el-form-item>
    <el-form-item prop="password">
      <el-input
        v-model="LoginFormList.password"
        prefix-icon="el-icon-phone"
        placeholder="请输入密码"
        show-password
      ></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="login">登录</el-button>
      <el-button type="primary">注册</el-button>
      <el-button
        type="primary"
        icon="el-icon-close"
        circle
        @click="reset"
      ></el-button>
    </el-form-item>
  </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      LoginFormList: {
        username: '',
        password: ''
      },
      RegFormList: {
        username: '',
        password: '',
        apassword: ''
      },
      LoginFormListRules: {
        username: [
          { required: true, message: '请输入用户名', triggle: 'blur' },
          {
            min: 4,
            max: 10,
            message: '长度不合法，请重新输入！',
            triggle: 'blur'
          }
        ],
        password: [
          { required: true, message: '请输入密码', triggle: 'blur' },
          {
            min: 6,
            max: 12,
            message: '长度不合法，请重新输入！',
            triggle: 'blur'
          }
        ]
      },
      RegFormListRules: {
        username: [
          { required: true, message: '请输入用户名', triggle: 'blur' },
          {
            min: 4,
            max: 10,
            message: '长度不合法，请重新输入！',
            triggle: 'blur'
          }
        ],
        password: [
          { required: true, message: '请输入密码', triggle: 'blur' },
          {
            min: 6,
            max: 12,
            message: '长度不合法，请重新输入！',
            triggle: 'blur'
          }
        ]
      }
    }
  },
  methods: {
    login () {
      this.$refs.LoginFormRef.validate(async (value) => {
        if (value) {
          const { data: res } = await this.$http.post(
            'login',
            this.LoginFormList
          )
          if (res.meta.status !== 200) return this.$message.error('登录失败')
          sessionStorage.setItem('token', res.data.token)
          this.$message.success('登录成功！')
          setTimeout(() => { this.$router.push('home') }, 1000)
        }
      })
    },
    goreg () {

    },
    reset () {
      console.log(this)
      this.$refs.LoginFormRef.resetFields()
    }
  }
}
</script>

<style lang="less" scoped>
div.container {
  background-color: #26496c;
  height: 100vh;
  div.login_box {
    width: 450px;
    height: 300px;
    background-color: #fff;
    position: relative;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    border: 2px solid #eee;
    box-shadow: 0px 0px 5px #eee;
    div.login_logo {
      width: 150px;
      height: 150px;
      padding: 5px;
      border-radius: 50%;
      line-height: 150px;
      border: 1px solid #eee;
      position: relative;
      left: 50%;
      transform: translate(-50%, -50%);
      img {
        width: 100px;
        height: 100px;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        border: 1px solid #eee;
        border-radius: 50%;
        background-color: #eee;
        box-shadow: 0px 0px 15px 20px #eee;
      }
    }
    .el-form {
      width: 100%;
      position: absolute;
      top: 85px;
      box-sizing: border-box;
      padding: 0px 10px;
      .el-input {
        box-sizing: border-box;
        width: 100%;
      }
      button.el-button {
        width: 100%;
        margin-left: 0;
      }
      button:first-child {
        margin-bottom: 3px;
      }
      button:last-child {
        width: 40px;
        position: absolute;
        top: -230px;
        right: -30px;
      }
    }
  }
}
</style>
