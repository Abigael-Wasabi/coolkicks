<script setup>
import axios from 'axios';
import router from '../../../router';

const Logout = async () => {
  const token = localStorage.getItem('token');
  try {
     await axios.post(
      'http://localhost:8000/api/user/logout',
      {},
      {
        headers: {
          Authorization: `Bearer ${token}`,
        },
      }
      );
    localStorage.removeItem('token')
    router.push('/')
  } catch (error) {
    console.log(error);
  }
};
</script>

<template>
    <button @click="Logout">Logout</button>
</template>

<style scoped>
button {
    background-color: red;
    padding: 10px 15px;
    font-size: 16px;
    border: 1px solid red;
    border-radius: 15px;
    color: #fff;
    cursor: pointer;
    transition: 0.5s ease-in-out;
}
button:hover {
    background-color: #fff;
    color: red;
    /* border: 1px solid red; */
}
</style>