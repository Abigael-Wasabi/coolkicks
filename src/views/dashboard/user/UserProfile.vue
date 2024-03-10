<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';
import profilePic from '../../../components/ProfilePic.vue'

const router = useRouter();

const logout = async () => {
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
    localStorage.removeItem('token');
    router.push('/');
  } catch (error) {
    console.log(error);
  }
};

</script>

<template>
  <v-layout>
    <v-app-bar title="User Dashboard"></v-app-bar>

    <v-navigation-drawer permanent>
      <v-list>
        <v-list-item to="#" title="Dashboard" prepend-icon="mdi-home" style="text-align: left;"></v-list-item>
        <v-list-item :to="{ name: 'user-profile' }" title="UserProfile" prepend-icon="mdi-book" style="text-align: left;"></v-list-item>
        <v-list-item :to="{ name: 'user-product' }" title="Products" prepend-icon="mdi-book" style="text-align: left;"></v-list-item>
       <v-list-item @click="logout" title="Logout" prepend-icon="mdi-logout" style="text-align: left;"></v-list-item>
      </v-list>
      <h4 class="mt-80 font-bold text-left">CORNER STORE</h4>
    </v-navigation-drawer>

    <v-main>
        <ProfilePic />
    </v-main>
  </v-layout>
</template>

<style scoped>
button {
  background-color: red;
  padding: 10px 15px;
  font-size: 16px;
  border: none;
  border-radius: 15px;
  color: #fff;
  cursor: pointer;
  transition: 0.5s ease-in-out;
}
button:hover {
  background-color: #fff;
  color: red;
  border: 1px solid red;
}
</style>
