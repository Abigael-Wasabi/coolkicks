<template>
  <div class="about">
    <ProductView />
    <ProductImages />
  </div>
  <FooterView/>
</template>

<script setup>
import ProductView from '../components/ProductDesc.vue';
import ProductImages from '../components/ProductImages.vue';
import FooterView from '../components/FooterView.vue'
</script>

<!-- <style scoped>
.about {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

@media screen and (max-width: 600px) {
  .about {
    padding: 60px;
    flex-direction: column-reverse;
    align-items: flex-center;
  }
}
</style> -->
