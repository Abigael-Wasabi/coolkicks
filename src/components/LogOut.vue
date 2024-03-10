<script setup>
import axios from 'axios';
import router from '../router';

const Logout = async () => {
  const token = localStorage.getItem('token');
  try {
     await axios.post(
      'http://localhost:8000/api/logout',
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
    border: none;
    border-radius: 15px;
    padding: 10px 20px;
    font-size: 16px;
    font-family: 'Courier New', Courier, monospace;
    color: #fff;
    transition: 0.3s ease;
}
button:hover {
    background-color: aliceblue;
    color: red;
    font-weight: bold;
    border: 1px solid red;
}
</style>