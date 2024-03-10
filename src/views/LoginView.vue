<script setup>
import axios from 'axios';
import { ref } from 'vue';
import '@/assets/styles/Login.scss'
import router from '../router';
import LoadingAnimation from '../components/LoadingAnimation.vue';

let loggedIn = ref(false);
let invalidCredentials = ref(false)

const user = ref({
  username: '',
  password: ''
});

const submitForm = async () => {
  loggedIn.value = true; // Set loading state to true before making the API call
  try {
    const response = await axios.post('http://localhost:8000/api/login', user.value);
    localStorage.setItem('token', response.data.token)
    loggedIn.value = true
    invalidCredentials.value = false

    if (response.data.role === true) {
      router.push('/admin');
    } else {
      router.push('/user');
    }
  } catch (error) {
    if(error.response.status === 401) {
      invalidCredentials.value = true
    }
    console.log(error);
  } finally {
    loggedIn.value = false;
  }
};

</script>

<template>
  <div class="login-form">
    <form @submit.prevent="submitForm">
      <fieldset>
        <legend>Login</legend>
        <div>
          <input type="text" name="" placeholder="username" v-model="user.username" required>
        </div>
        <div>
          <input type="password" name="" placeholder="password" v-model="user.password" required>
        </div>
        <p v-if="invalidCredentials" style="color: red; font-weight: bold;">Invalid Username or password</p>
        <button type="submit">Login</button>
        <RouterLink to="/signup">New member, signup</RouterLink>
        <div v-if="loggedIn">
          <LoadingAnimation />
        </div>
      </fieldset>
    </form>

  </div>
</template>
