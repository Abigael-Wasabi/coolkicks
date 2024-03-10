<template>
    <div class="profile">
      <section class="pic">
        <img v-if="profile" :src="profile" alt="profile pic"> 
        <img v-else-if="!profile" src="@/assets/images/default-profile.png" alt="default profile image">
        <!-- <img  src="@/assets/images/default-profile.png" alt="default profile image"> -->
      </section>
      <section class="upload">
        <input type="file" @change="onFileSelected" v-if="updateButtonClicked" placeholder="update">
        <button @click="updateClicked">Update</button>
      </section>
    </div>
  </template>
  
  <script setup>
  import axios from 'axios';
  import { ref } from 'vue';
  
  const updateButtonClicked = ref(false)
  const selectedFile = ref(null);
  const profile = ref(null); 
  
  
  const onFileSelected = event => {
    selectedFile.value = event.target.files[0];
  };
  
  const onFileUpload = async () => {
    const token = localStorage.getItem('token');
    const fd = new FormData();
    fd.append('image', selectedFile.value);
  
    try {
      const response = await axios.post('http://localhost:8000/api/user-profile-pictures/', fd, {
        headers: {
          Authorization: `Bearer ${token}`
        }
      });
      console.log(response);
      // Assuming the API returns the URL to the uploaded image in the response
      profile.value = response.data.profilePic;
      updateButtonClicked.value = false
    } catch (error) {
      console.error('Error uploading image:', error);
    }
  };
  
  const getProfilePic = async () => {
    const token = localStorage.getItem('token');
  
    try {
      const response = await axios.get('http://localhost:8000/api/user-profile-pictures/', {
        headers: {
          Authorization: `Bearer ${token}`
        }
      });
      console.log(response);
      profile.value = response.data.profilePic;
    } catch (error) {
      console.error('Error fetching profile picture:', error);
    }
  };
  
  const updateClicked = () => {
    updateButtonClicked.value = true;
    onFileUpload()
  }
  
  
  getProfilePic();
  </script>
  
  <style scoped>
  .profile {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin: 20px;
    padding: 0 150px;
  }
  .pic {
    height: 50px;
    width: 50px;
    border-radius: 50%;
    border: 1px solid rgb(126, 123, 123);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  img {
    height: 70px;
    width: 70px;
    border-radius: 50%;
  }
  
  .upload button {
    background-color: green;
    cursor: pointer;
    padding: 10px 40px;
    transition: 0.3s ease-in-out;
  }
  .upload button:hover {
    color: green;
    background-color: #fff;
  }
  </style>
  