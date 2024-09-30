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
  // console.log(`${api}/users/sign_up`)
  const res = await axios.post(`${api}/users/sign_up`, signupField.value)
  console.log(res)
}

// 登入
const resToken = ref('')
const signinField = ref({
  email: '',
  password: ''
})

const singin = async () => {
  // console.log(`${api}/users/sign_in`)
  const res = await axios.post(`${api}/users/sign_in`, signinField.value)
  console.log(res)
  resToken.value = res.data.token
}

// 驗證
const verifyField = ref('')
const verifyResult = ref('')
const verify = async () => {
  const res = await axios.get(`${api}/users/checkout`, {
    headers: {
      authorization: verifyField.value
    }
  })
  console.log(verifyField)
  console.log(res)
  verifyResult.value = res.data
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
  <div>
    <h2>登入</h2>
    <input type="email" placeholder="Email" v-model="signinField.email" />
    <input type="text" placeholder="Password" v-model="signinField.password" />
    <button type="button" @click="singin">登入</button>
  </div>
  {{ signinField }}
  {{ resToken }}

  <hr />
  <h2>驗證</h2>
  <input type="text" placeholder="Token" v-model="verifyField" />
  <button type="button" @click="verify">驗證</button>
  {{ verifyResult }}

  <hr />
  <h2>登出</h2>
</template>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Microsoft JhengHei', Roboto,
    'Helvetica Neue', Arial, sans-serif;
}
</style>
