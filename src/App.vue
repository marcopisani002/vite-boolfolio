<script>
import TheHeader from "./TheHeader.vue";


export default {
  components: { TheHeader },
  data() {
    return {
 
    };
  },
 
};

</script>

<template>
  <TheHeader></TheHeader>
  <!-- In Blade usavamo lo @yield("content") -->
  <!-- In vue-router usiamo il tag router-view -->
   <router-view></router-view> 

</template>

<style lang="scss">
@use "main.scss";

body {
  min-height: 100vh;

  background: linear-gradient(12deg, rgb(20, 193, 223) 0%, rgba(10, 170, 143, 0.786) 50%, rgb(25, 224, 148) 100%);
}</style>
