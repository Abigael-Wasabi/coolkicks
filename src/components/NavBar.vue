<template>
    <nav>
      <RouterLink to="/">
        <img src="@/assets/images/coolkick.jpg" alt="Logo" id="logo"/>
      </RouterLink>
      <ul :class="{ active: active, navMenu: true }">
        <li @click="unToggle">
          <RouterLink to="/">Home</RouterLink>
        </li>
        <li @click="unToggle">
          <RouterLink to="/product">Product</RouterLink>
        </li>
        <li @click="unToggle">
          <RouterLink to="/contact">Contact</RouterLink>
        </li>
      </ul>
      <ul :class="{active: active, buttons: true}">
        <li class="cartIcon">
          <RouterLink to="/cart">
          <img src="@/assets/images/cart.png"  alt="cart-icon">
        </RouterLink>
        </li>
        <li @click="unToggle" class="btn1">
          <RouterLink to="/signup" class="signup">Signup</RouterLink>
        </li>
       
        <li @click="unToggle" class="btn2">
          <RouterLink to="/login" class="login">Login</RouterLink>
        </li>
      </ul>
      <div :class="{ hamburger: true, active: active }" @click="toggle">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </div>
    </nav>
    <section class="hr"> <hr></section>
  </template>
  
  <script>
  import { RouterLink } from 'vue-router';
  import '../assets/styles/Navbar.scss'
  
  
  export default {
    name: 'NavBar',
    components: {
      RouterLink,
    },
  
    data() {
      return {
        active: false,
      };
    },
  
    methods: {
      toggle() {
        this.active = !this.active; //
      },
      unToggle() {
        this.active = false;
      }
    },
  };
  </script>

