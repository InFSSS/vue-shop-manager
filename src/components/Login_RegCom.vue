<template>
    <el-form
    ref="RegFormRef"
    :model="RegFormList"
    :rules="RegFormListRules"
  >
    <el-form-item prop="username">
      <el-input
        v-model="RegFormList.username"
        prefix-icon="el-icon-user-solid"
        placeholder="请输入用户名"
      ></el-input>
    </el-form-item>
    <el-form-item prop="password">
      <el-input
        v-model="RegFormList.password"
        prefix-icon="el-icon-phone"
        placeholder="请输入密码"
        show-password
      ></el-input>
    </el-form-item>
    <el-form-item prop="apassword">
      <el-input
        v-model="RegFormList.apassword"
        prefix-icon="el-icon-phone"
        placeholder="请输入密码"
        show-password
      ></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary"><router-link to="/logincom">登录</router-link></el-button>
      <el-button
        type="primary"
        icon="el-icon-close"
        circle
        @click="reset"
      ></el-button>
    </el-form-item>
  </el-form>
</template>
