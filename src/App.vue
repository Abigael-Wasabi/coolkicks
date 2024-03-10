<script setup>
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue';
import './assets/styles/App.scss'
</script>

<template>
  <header>
    <div class="wrapper">
      <NavBar />
    </div>
  </header>

  <RouterView />
</template>
