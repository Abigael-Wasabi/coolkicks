<template>
 <h1 class="font-bold mt-6" style="text-align: center;">Drop us a line</h1>

   <a target='_blank' href="mailto:coolkicks254@gmail.com" rel="noreferrer" style="display: flex; align-items: center;">
          <span style="margin-left: 200px; color: salmon;"><FontAwesomeIcon :icon="faEnvelope" size="3x" /></span>
                    <span style="margin-left: 30px; color: black">coolkicks254@gmail.com</span>
        </a><br>
        <hr class="smallhr">

        <a target='_blank' href="+254 7 123 456 07" rel="noreferrer" style="display: flex; align-items: center;">
          <span style="margin-left: 200px; color: salmon;"><FontAwesomeIcon :icon="faPhone" size="3x" /></span>
                   <span style="margin-left: 30px; color: black">+254 7 123 456 07</span>
        </a><br> 
        <hr class="smallhr">

        <a target='_blank' href="+254 7 123 456 07" rel="noreferrer" style="display: flex; align-items: center;">
          <span style="margin-left: 200px; color: salmon;"><FontAwesomeIcon :icon="faMapMarkerAlt" size="3x" /></span>
          <span style="margin-left: 30px; color: black">Moi Avenue, Twins Tower</span>
        </a>
        <hr class="smallhr">

        <a></a><br>
        <a target='_blank' href="+254 7 123 456 07" rel="noreferrer" style="display: flex; align-items: center;">
          <span style="margin-left: 200px; color: salmon;"><FontAwesomeIcon :icon="faWhatsapp" size="3x" /></span>
                    <span style="margin-left: 30px; color: black;">+254 7 123 456 07</span>
        </a>
        <hr class="smallhr">
     <header>
  </header>
    <div>
    </div>
    <FooterView/>
</template>

<script setup>
import FooterView from '../components/FooterView.vue'
import { faEnvelope, faPhone, faMapMarkerAlt } from '@fortawesome/free-solid-svg-icons'
import { faWhatsapp } from '@fortawesome/free-brands-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
</script>

<style scoped>
.smallhr {
  width: 80%; 
  margin: 0 auto; 
}
</style>