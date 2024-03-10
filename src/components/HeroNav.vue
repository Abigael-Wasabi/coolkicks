<template>
    <div class="bg-black py-16 sm:py-20 lg:py-24 px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <div class="flex flex-col-reverse md:flex-row items-center justify-between">
          <!-- Text Section -->
          <div class="md:w-1/2 text-white text-left md:text-center">
            <h1 class="text-3xl sm:text-4xl lg:text-5xl font-bold mb-4"> Fresh Vegetable Store</h1>
            <p class="text-base sm:text-lg lg:text-xl">Discover our affordbale prices anytime, anywhere.</p>
            <p class="text-base sm:text-lg lg:text-xl mt-4">Experience the joy of using having the best farm produced veges in town.</p>
            <router-link to="/signup">
        <button class="mt-6 py-2 px-6 bg-green-500 hover:bg-green-800 text-white font-bold rounded-full items-center">Get Started</button>
        <button class="mt-6 py-2 px-6 bg-green-500 hover:bg-green-800 text-white font-bold rounded-full ml-6 items-center">Products</button>
        </router-link>
          </div>
  
          <!-- Image Section -->
          <div class="md:w-1/2 mt-8 mb-22 md:mt-0">
            <img src="../assets/images/brown1.jpg" alt="Music App Image" class="w-full h-auto rounded-lg shadow-lg">
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  </script>
  
