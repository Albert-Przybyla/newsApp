<script setup>
 import { RouterLink, RouterView } from 'vue-router'
 import Modal from "./components/Modal.vue"
 import Headerc from "./components/Headerc.vue"
</script>

<template>
  <!-- nav -->
  <div id="bigNav">
  <Headerc/>
  </div>
  <div id="smallNav">
    <button @click="openSmallNav"><p>menu</p></button>
    <div class="smalMenu" v-if="open">
      <Headerc/>
    </div>
  </div>
  <!--     -->
  <RouterView />
  <div v-if="showModal">
  <Modal :header="header" :text="text" :theme="theme" @close="closeModal"/>
  </div>
</template>
<script>
export default {
  name: 'App',
  data(){
    return {
      open: false,
      header: "hello in news world",
      text: "nice to meet you",
      theme: "welcome",
      showModal: true,
      components: { Modal },
      components: { Headerc },
    }
  },
  Methods: {
    openSmallNav(){
      this.open = !this.open;
      // console.log(open)
    },
    closeModal(){
      showModal = false
    },
  }

}
</script>

<style scoped>



@media (max-width: 1024px) {
  #bigNav{
    display: none;
  }
}

@media (min-width: 1025px) {
  #smallNav{
    display: none;
  }
}
</style>
