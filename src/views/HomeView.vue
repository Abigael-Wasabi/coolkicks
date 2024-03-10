<script setup>
import '../assets/styles/Home.scss'
import HeaderText from '../components/HeaderText.vue'
import HomeProduct from '../components/HomeProduct.vue';
import FooterView from '../components/FooterView.vue'
</script>

<template>
  <main>
    <section class="home bg-blue">
      <HeaderText />
      <img src="@/assets/images/coolkick.jpg" alt="Sneaker" id="headerImg">
    </section>
    <section class="products">
      <HomeProduct />
      <FooterView/>
    </section>
  </main>
  
</template>

