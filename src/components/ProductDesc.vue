<template>
    <section class="product-desc">
        <h5 style="text-align: center;">At one's Disposal</h5>
        <h1 style="text-align: center;"><span>{{ productName }}</span>CoolKicks<span>16.0</span></h1>
        <article class="sizes">
            <h3 style="text-align: center;">Pick a Size</h3>
            <figure style="text-align: center;">
                <button :class="{active: active[0], btn: true}" @click="toggle(0)">7</button>
                <button :class="{active: active[1], btn: true}" @click="toggle(1)">8</button>
                <button :class="{active: active[2], btn: true}" @click="toggle(2)">9</button>
                <button :class="{active: active[3], btn: true}" @click="toggle(3)">10</button>
                <button :class="{active: active[4], btn: true}" @click="toggle(4)">11</button>
                <button :class="{active: active[5], btn: true}" @click="toggle(5)">12</button>
            </figure>
        </article>
        <article class="quantity" style="justify-content: center;">
            <button class="add" @click="increment">
                <img src="@/assets/images/plus.png" alt="plus-icon">
            </button>
            <p>{{ count }}</p>
            <button class="minus" @click="decrement" :disabled="count === 0">
                <img src="../assets/images/minus.png" alt="minus-icon">
            </button>
        </article>
        <article class="cart">
            <button onclick=""
            style="margin: 0 auto;" class="addToCart">Add To Cart</button>
            <p v-if="count > 0">Total: <span>${{ total }}</span></p>
        </article>
        <!-- <img :src="selectedImage" alt="Product Image" class="main-image"> -->
    </section>
</template>

<script setup>
import { ref } from 'vue';
import '@/assets/styles/ProductDesc.scss'

const productName = ref('yeezys'); //default product name
const selectedImage = ref('purple.jpg'); //default selected image

const handleImageSelected = (index) => {
  // Updatingproduct info based on the selected thumbnail index
  productName.value = ''; //corresponding product name
  selectedImage.value = ''; //the selected image path
};

const count = ref(0);
const active = ref([true, false, false, false, false, false,false, false, false, false, false, false, false, false, false]);
var total = 0;

function increment() {
    count.value++;
    total = count.value * 200;
}

function decrement() {
   count.value--;
   total = count.value * 200;
}

function toggle(index) {
    active.value = active.value.map((value, i) => i === index);
}
</script>

<style scoped>
.main-image {
  max-width: 100px; 
  max-height: 300px;
  display: block;
  margin: 0 auto;
}
</style>