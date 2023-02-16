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
   
</template>

<style lang="scss">
@use "main.scss";

body {
    min-height: 100vh;
 
    background: linear-gradient(12deg, rgb(20, 193, 223) 0%, rgba(10, 155, 10, 0.786) 50%, rgb(25, 224, 148) 100%);
  }
</style>
