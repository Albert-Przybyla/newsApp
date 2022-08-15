<script setup>
 import { RouterLink, RouterView } from 'vue-router'
 import home from "./components/home.vue"
</script>


<template>
  <home/>
  <RouterView />
</template>
<script>
export default {
  name: 'App',
  data(){
    return {
    }
  },
  Methods: {

  },

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;600&display=swap');

  * {
    box-sizing: border-box;
  }

  body {
    font-family: 'Oswald', sans-serif;
    margin: 0;
    padding: 0;
  }

</style>
