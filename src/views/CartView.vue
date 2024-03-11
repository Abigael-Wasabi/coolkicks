<template>
    <div class="cart-container">
      <h2>Your Shopping Cart</h2>
      <div v-if="cartItems.length === 0">
        <p>Oops! Your cart is empty.</p>
        <router-link to="/product">Continue Shopping</router-link>
      </div>
      <div v-else>
        <div v-for="item in cartItems" :key="item.id" class="cart-item">
          <div class="item-info">
            <img :src="item.image" :alt="item.name" class="item-image">
            <div class="item-details">
              <h3>{{ item.name }}</h3>
              <p>Price: ${{ item.price }}</p>
              <p>Quantity: {{ item.quantity }}</p>
            </div>
          </div>
          <div class="item-actions">
            <button @click="removeItem(item.id)">Remove</button>
          </div>
        </div>
        <div class="cart-summary">
          <p>Subtotal: ${{ calculateSubtotal() }}</p>
          <router-link to="/checkout">Proceed to Checkout</router-link>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        cartItems: [
          { id: 1, name: "Sneaker 1", price: 50, quantity: 2, image: "sneaker1.jpg" },
          { id: 2, name: "Sneaker 2", price: 60, quantity: 1, image: "sneaker2.jpg" }
        ]
      };
    },
    methods: {
      removeItem(itemId) {
        this.cartItems = this.cartItems.filter(item => item.id !== itemId);
      },
      calculateSubtotal() {
        return this.cartItems.reduce((total, item) => total + (item.price * item.quantity), 0);
      }
    }
  };
  </script>
  
  <style scoped>
  .cart-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .item-info {
    display: flex;
    align-items: center;
  }
  
  .item-details {
    margin-left: 20px;
  }
  
  .item-image {
    width: 100px;
    height: 100px;
    object-fit: cover;
  }
  
  .item-actions button {
    background-color: #f44336;
    color: white;
    border: none;
    padding: 8px 16px;
    cursor: pointer;
  }
  
  .cart-summary {
    margin-top: 20px;
    text-align: center;
  }
  
  .cart-summary p {
    margin-bottom: 10px;
  }
  
  .cart-summary a {
    background-color: #4caf50;
    color: white;
    text-decoration: none;
    padding: 10px 20px;
    border-radius: 4px;
  }
  </style>
  