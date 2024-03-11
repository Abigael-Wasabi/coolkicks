<template>
    <div class="product">
       <div class="product-image">
          <img
          :src="require('@/assets/' + data.images[slideIndex] + '.png')"
           alt="product"
          />
        </div>
        <div class="product-details">
          <div>
            <h1 class="product-name">
                {{data.names[slideIndex]}}
            </h1>
            <h1 class="price">
              $<span class="product-price"> 
                {{data.prices[slideIndex]}} 
            </span>, <sup>99</sup>
            </h1>
            <div class="details">
              <div class="options">
                <b class="product-option-title">
                  {{data.optionTitles[slideIndex]}}
                </b>
                <ul class="option-list">
                  <li
                    v-for="(option, index) in data.options[slideIndex]"
                    :key="index"
                    class="option">
                    :class ="[active === index ? 'option-active' : '']"
                    @click="() => active = index">
                    {{option}}
                  </li>
                </ul>
            </div>
             <ProgressBar :count="count" :data="data" :slideIndex="slideIndex" />
            </div>
            <div class="buttons">
              <button type="button" class="btn-primary"><b>Add To Cart</b></button>
              <button type="button" class="btn-secondary">
                <i class="fas fa-heart"></i>Add       </button>
          </div>
        </div>
    </div>
    </div>
</template>

<script>
import ProgressBar from './ProgressBar.vue';
export default {
    name: 'ProductDetails',
    props: {
      data: Object,
      slideIndex: Number,
      count: Number,
      active: Number
},
components: {
  ProgressBar
}
} 
</script>

<style scoped>
.product {
    position: relative;
    z-index: 2;
    display: grid;
    grid-template-columns: 1fr 1fr;
    height: 100%;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: #103248;
}
.product-details {
display: flex;
justify-content: flex-start;
align-items: center;
}

.product-image {
display: flex;
justify-content: center;
align-items: center;
}
.product-image img {
width: 70%;
filter: drop-shadow(00 3em Irgba(0, 0, 0, 0.3));
}
.product h1 {
font-size: 2.8em;
margin: 0;
}
.product.price {
font-weight: 300;
margin: 0.2em 0;
}
.details {
display: flex;
justify-content: flex-start;
align-items: center;
margin: 2em 0;
}
.product-option-title {
margin-left: 0.5em;
}
.options {
padding: 1em 1.5em 1em 0;
margin: 1em 0;
border-right: 1px #103248 solid;
justify-self: flex-start;
}
.options ul {
list-style: none;
margin: 0.5em 0;
padding: 0;
}
.options ul li {
display: inline-block;
margin-right: 0.5em;
padding: 0.5em;
border-radius: 3em;
cursor: pointer;
}
.option-active {
border: 1px #12c141 solid;
}
.buttons button {
border: none;
cursor: pointer;
text-transform: uppercase;
}
.btn-primary {
color: #fff;
background:#12c141;
font-size: 0.9em;
padding: 1em 2em;
border-radius: 3em;
box-shadow: 0 1em 2em #12c141;
margin-right: 1em;
transition: 0.3s;
}
.btn-primary:hover {
background:#fff;
color: #12c141;
}
.btn-secondary {
background: none;
border: none;
}
.btn-secondary i {
color: #10afcf;
margin-right: 0.5em;
}
@media screen and (max-width: 880px) {
.product-details {
    justify-content: center;
}
.details{
    flex-direction: column;
}
.product{
    grid-template-columns: 1fr;
}
.product-image img {
    width: 50%;
}
.options {
    border-right: none;
    padding-right: 0;
}
.buttons button {
    display: block;
    margin: 2.5em auto;
}
}
</style>