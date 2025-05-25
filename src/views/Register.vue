<template>
  <div>
    <h1>Register Page</h1>
    <form @submit.prevent="registerUser">
      <h2>Register</h2>
      <label>Name</label>
      <input type="text" placeholder="Name" v-model="form.name" />
      <label>Email</label>
      <input type="email" placeholder="Email..." v-model="form.email" />
      <label>Password</label>
      <input type="password" placeholder="Password..." v-model="form.password" />
      <button type="submit">Register</button>
    </form>
  </div>
</template>

<script lang="ts" setup>
import axios from 'axios'
import { reactive } from 'vue'

const form = reactive({
  name: '',
  email: '',
  password: ''
})

const url = 'https://683306cfc3f2222a8cb4b199.mockapi.io/api/form/users'

const registerUser = async () => {
  if (!form.name || !form.email || !form.password) {
    alert('Please fill in all fields.')
    return
  }

  try {
    const response = await axios.post(url, form)
    alert('Registered successfully!')
    console.log(response.data)
    window.location.href = '/login' // หรือใช้ router.push ถ้าใช้ Vue Router
  } catch (error) {
    console.error('Error registering:', error)
    alert('Registration failed.')
  }
}
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  width: 400px;
  padding: 20px;
  border: 1px solid #646cff;
  border-radius: 10px;
  gap: 10px;
  margin: auto;
}

input {
  padding: 12px;
  border-radius: 5px;
}

button {
  margin-top: 10px;
}
</style>
