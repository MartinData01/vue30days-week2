<script setup>
import { ref } from 'vue'
import axios from 'axios'

const api = 'https://todolist-api.hexschool.io'

// 註冊
const signupField = ref({
  email: '',
  password: '',
  nickname: ''
})

const singup = async () => {
  console.log(`${api}/users/sign_up`)
  const res = await axios.post(`${api}/users/sign_up`, signupField.value)
  console.log(res)
}
</script>

<template>
  <h1>Todo List API</h1>
  <div>
    <h2>註冊</h2>
    <input type="email" placeholder="Email" v-model="signupField.email" />
    <input type="text" placeholder="Password" v-model="signupField.password" />
    <input type="text" placeholder="Nickname" v-model="signupField.nickname" />
    <button type="button" @click="singup">註冊</button>
  </div>
  {{ signupField }}
  <hr />
  <h2>登入</h2>

  <hr />
  <h2>驗證</h2>

  <hr />
  <h2>登出</h2>
</template>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Microsoft JhengHei', Roboto,
    'Helvetica Neue', Arial, sans-serif;
}
</style>
