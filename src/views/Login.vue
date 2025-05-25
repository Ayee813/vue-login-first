<template>
  <div>
    <!-- <div class="start">
    </div> -->
    <h1>Login Page</h1>
    <form>
      <h2>Login</h2>
      <label>Name</label>
      <input type="text" placeholder="Name" v-model="form.name">
      <label>Email</label>
      <input type="email" placeholder="Email..." v-model="form.email">
      <label>password</label>
      <input type="password" placeholder="password..." v-model="form.password">
      <button @click="HandleLogin">Submit</button>
    </form>
  </div>
</template>

<script lang="ts" setup>
import axios from 'axios';
import { reactive, Reactive } from 'vue';

const form = reactive({
  name: '',
  email: '',
  password: '',
})

interface User {
  name: string;
  email: string;
  password: string;
}
const state = reactive<{users: User[]}>(
  {
    users: []
  }
)

const url = 'https://683306cfc3f2222a8cb4b199.mockapi.io/api/form/users'

const fetchData = async () => {
  try {
    const response = await axios.get(url)
    state.users = response.data;
    console.log(response.data);
    
  }
  catch (error){
    console.error(error);
    
  }

}



</script>
<style>
form {
  display: flex;
  justify-items: center;
  align-items: center;
  flex-direction: column;
  width: 400px;
  height: 380px;
  border: 1px solid #646cff;
  border-radius: 10px;
  gap: 5px;
}

label {
  text-align: start;
}

input {
  padding: 12px;
  border-radius: 5px;
}

button {
  margin-top: 10px;
}

.start {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 150px;
  height: 50px;
  background-color: #646cff;
  margin: 40px;
  transform: translate(-50%, -50%);
  border-radius: 20px;
}

.start::before {
  content: "Get started";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>