<template>
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
      <el-button type="primary" @click="goreg"><router-link to="/regcom">注册</router-link></el-button>
      <el-button
        type="primary"
        icon="el-icon-close"
        circle
        @click="reset"
      ></el-button>
    </el-form-item>
  </el-form>
</template>
