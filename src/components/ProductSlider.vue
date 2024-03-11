<template>
    <section class="product-slider">
        <img src="../assets/images/coolkick.jpg" class="logo"/>
        <div class="card">
            <div class="panel-1"
            :style="'background:url(' + require('@/assets/images/' + 
            data.backgrounds[slideIndex] + '.jpg') + ')'"></div>
            <div class="panel-2"></div>
            <ProductDetails
            :data ="data"
            :slideIndex="slideIndex"
            :count ="count"
            :active = "active"
            />
            <div class="arrow-left" @click="count = 0; updateCount(); slideLeft();">
                <i class="fas fa-arrow-left"></i>
            </div>
            <div class="arrow-right" @click="count = 0; updateCount(); slideRight();">
                <i class="fas fa-arrow-right"></i>
            </div>
        </div>
    </section>
</template>

<script>
// import FooterView from '../components/FooterView.vue'
import ProductDetails from './ProductDetails.vue'
export default {
    name: 'ProductSlider',
    data () {
        return {
            slideIndex : 0,
            count: 0,
            active: 4,
            data:{
                images:[
                    "yellow.jpg",
                    "white",
                    "red",
                    "purple",
                    "pink",
                    "navy",
                ],
                names: [
                    "j1",
                    "j2",
                    "j3",
                    "j4",
                    "j5",
                    "j6",
                ],
                prices: [
                    "1",
                    "2",
                    "3",
                    "4",
                    "5",
                    "6",
                ],
                optionTitles: [
                    "service",
                    "ser",
                    "serv",
                    "servi",
                    "servic",
                    "seice",
                ],
                options: [
                    ["a","z"],
                    ["b","x"],
                    ["c","g"],
                    ["d","j"],
                    ["e","m"],
                    ["u","i"],
                ],
                progress: [67,23,45,56,67,78],
                backgrounds: [
                    "background1",
                    "background2",
                    "background3",
                ],
            }
        }
    },
    components: {
        ProductDetails
    },
    methods: {
      updateCount() {
      const target = this.data.progress [this.slideIndex]
      if (this.count < target) {
        this.count++
        setTimeout(this.updateCount, 30)
      } else {
        this.count = target
      }
     },
     slideLeft() {
        this.slideIndex--
        if(this.slideIndex < 0) {
           this.slideIndex = this.data.names.length - 1
        }
       },
       slideRight() {
        this.slideIndex++
        if(this.slideIndex > this.data.names.length-1) {
          this.slideIndex = 0
        }
       }
    },
    created () {
        this.updateCount();
    }
}
</script>

<style scoped>
.product-slider{
    padding: 2em;
    background: linear-gradient(-45deg, #abd7d7, #e8ecf0);
    display: flex;
    justify-content: center;
    align-items: center;
}
.logo{
    width: 40%;
    height: 90%;
    object-fit: cover;
    position: absolute;
    top: 50%;
    right: 0;
    transform: translateY(-50%);
}
.card{
    padding: 2em;
    width:90vw;
    height: 90vh;
    min-height: 35em;
    max-width: 1050px;
    position: relative;
}
.panel-1,
.panel-2 {
    position: absolute;
    box-shadow: 0 0 4em 3em rgba(0,0,0,0.1);
    border-radius: 2em;
    top: 50%;
    transform: translateY(-50%);
}
.panel-1 {
  background-repeat: no-repeat;
  background-position: center;
  background-size:cover;
  right: 0;
  width: 80%;
  height: 90%;
  overflow:hidden;
  z-index:1;
  transition: 0.3s;
}
.panel-1::before{
    content: '';
    background: linear-gradient(45deg,
     rgb(255,255,255) 0%,
     rgb(221,223,227) 40%,
     rgba(244,223,227, 0.8));
     position: absolute;
     top: 0;
     left: 0;
     width: 100%;
     height: 100%;
}
.panel-2 {
   background: linear-gradient(
     #1bb843 0%,
     #1ba7a1 100%
);
left: 0;
width: 50%;
height: 100%;
z-index: 0;
overflow: hidden;
}

.panel-2::before {
content: '';
background: url(../assets/yellow.jpg);
background-position: center;
background-size: contain;
background-repeat: no-repeat;
width: 100%;
height: 100%;
position: absolute;
top: 50%;
left: -5em;
transform: translateY(-50%) rotate(-90deg);
z-index: 2;
}
.arrow-Left,
.arrow-right {
position: absolute;
top: 50%;
transform: translateY(-50%);
width: 4em;
height: 4em;
background:#10afcf;
color: #fff;
border-radius: 50%;
text-align: center;
line-height: 4.2em;
z-index: 2;
transition: 0.3s;
cursor: pointer;
}

.arrow-left i,
.arrow-right i { font-size: 1.5em; }
.arrow-Left { left: 1em; }
.arrow-right { right: 1em;
}

.arrow-left:hover,
.arrow-right:hover {
background:#fff;
color: #10afcf;
}
@media screen and (min-width: 1000px) {
.arrow-Left {
left: 2em; 
}
.arrow-right {
right: -2em;
}
}

@media screen and (max-width: 880px) {
panel-1, .panel-2 {
display: none;
}
.card {
background: linear-gradient( 45deg,
   rgb(255, 255, 255) 0%,
   rgb(221, 223, 227) 40%,
   rgba(244, 255, 245, 0.8)
);
text-align: center;
height: initial;
padding: 3em 2em 1em 2em;
border-radius: 2em;
} 
.card h1 {
    margin-top:1em;
}
@media screen and (max-width:700px) {
    .product-slider {
        font-size: 13px;
    }
}
}
</style>