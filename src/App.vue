<script setup>
 import { RouterLink, RouterView } from 'vue-router'
 import Modal from "./components/Modal.vue"
 import home from "./components/home.vue"
</script>

<template>
  <home/>
  <RouterView />
  <div v-if="showModal">
  <Modal :header="header" :text="text" :theme="theme" @close="showModal = false"/>
  </div>
</template>
<script>
export default {
  name: 'App',
  data(){
    return {
      header: "hello in news world",
      text: "nice to meet you",
      theme: "welcome",
      showModal: true,
      components: { Modal },
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
