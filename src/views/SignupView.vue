<script setup>
import '@/assets/styles/Signup.scss'
import { ref } from 'vue';
import axios from 'axios';
import router from '../router';
import FooterView from '../components/FooterView.vue';

const user = ref({
  username: '',
  email: '',
  password: ''
})

const submitForm = async () => {
  try {
    const response = await axios.post('http://localhost:8000/api/signup', user.value);
    if(response) {
      router.push('/login')
    }
  } catch (error) {
    console.log(error);
  }
}
</script>

<template>
  <div class="signup-form">
    <form @submit.prevent="submitForm">
      <fieldset>
        <legend>Sign Up</legend>
        <div>
          <label for="username">Username:</label><br>
          <input type="text" id="username" v-model="user.username">
        </div>
        <div>
          <label for="email">Email:</label><br>
          <input type="email"  id="email" v-model="user.email">
        </div>
        <div>
          <label for="password">Password:</label><br>
          <input type="password"  id="password" v-model="user.password">
        </div>
        <button type="submit">Sign Up</button>
        <RouterLink to="/login">Already having an account? Login</RouterLink>
      </fieldset>
    </form>
  </div>
  <FooterView/>
</template>
