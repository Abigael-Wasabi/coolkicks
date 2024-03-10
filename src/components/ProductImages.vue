<template>
    <section class="images">
        <article class="main-images">
            <img v-if="active[0]" :src="thumb1" alt="purple">
            <img v-if="active[1]" :src="thumb2" alt="blue">
            <img v-if="active[2]" :src="thumb3" alt="red">
            <img v-if="active[3]" :src="image1" alt="brown">
            <img v-if="active[4]" :src="image2" alt="white">
            <img v-if="active[5]" :src="image3" alt="black">
            <img v-if="active[6]" :src="image4" alt="beige">
            <img v-if="active[7]" :src="image5" alt="gray">
            <img v-if="active[8]" :src="image6" alt="pink">
            <img v-if="active[9]" :src="image7" alt="green">
            <img v-if="active[10]" :src="image8" alt="yellow">
            <img v-if="active[11]" :src="image9" alt="navy">
            <img v-if="active[12]" :src="image10" alt="plain">
        </article>
        <article class="thumbnails">
            <img :src="thumb1" :class="{active: active[0], thumnail: true}" @click="toggleActive(0)" alt="purple">
            <img :src="thumb2" :class="{active: active[1], thumnail: true}" @click="toggleActive(1)" alt="blue">
            <img :src="thumb3" :class="{active: active[2], thumnail: true}" @click="toggleActive(2)" alt="red">
            <img :src="image1" :class="{active: active[3], thumnail: true}" @click="toggleActive(3)" alt="brown">
            <img :src="image2" :class="{active: active[4], thumnail: true}" @click="toggleActive(4)" alt="white">
            <img :src="image3" :class="{active: active[5], thumnail: true}" @click="toggleActive(5)" alt="black">
            <img :src="image4" :class="{active: active[6], thumnail: true}" @click="toggleActive(6)" alt="beige">
            <img :src="image5" :class="{active: active[7], thumnail: true}" @click="toggleActive(7)" alt="gray">
            <img :src="image6" :class="{active: active[8], thumnail: true}" @click="toggleActive(8)" alt="pink">
            <img :src="image7" :class="{active: active[9], thumnail: true}" @click="toggleActive(9)" alt="green">
            <img :src="image8" :class="{active: active[10], thumnail: true}" @click="toggleActive(10)" alt="yellow">
            <img :src="image9" :class="{active: active[11], thumnail: true}" @click="toggleActive(11)" alt="navy">
            <img :src="image10" :class="{active: active[12], thumnail: true}" @click="toggleActive(12)" alt="plain">
        </article>
    </section>
</template>

<script setup>
import '@/assets/styles/ProductImages.scss';
import thumb1 from '@/assets/images/purple.jpg';
import thumb2 from '@/assets/images/blue.jpg';
import thumb3 from '@/assets/images/red.jpg';
import image1 from '@/assets/images/brown.jpg';
import image2 from '@/assets/images/white.jpg';
import image3 from '@/assets/images/black.jpg';
import image4 from '@/assets/images/beige.jpg';
import image5 from '@/assets/images/gray.jpg';
import image6 from '@/assets/images/pink.jpg';
import image7 from '@/assets/images/green.jpg';
import image8 from '@/assets/images/yellow.jpg';
import image9 from '@/assets/images/navy.jpg';
import image10 from '@/assets/images/plain.jpg';
import { ref } from 'vue';

const active = ref([true, false, false])
function toggleActive(index) {
    active.value = active.value.map((value,i) => i === index)
}

</script>
