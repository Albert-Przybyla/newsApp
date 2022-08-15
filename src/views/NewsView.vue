<script setup>
import axios from 'axios';
import Item from '@/components/homeItem.vue';
import Modal from "@/components/Modal.vue"
</script>

<template>
  <main>
    <select
    v-model="selected"
    @input="show">
      <option>home</option><option> arts </option><option> automobiles </option><option> books </option><option> business </option><option> fashion </option><option> food </option><option> health </option><option> home </option><option> insider </option><option> magazine </option><option> movies </option><option> nyregion </option><option> obituaries </option><option> opinion </option><option> politics </option><option> realestate </option><option> science </option><option> sports </option><option> sundayreview </option><option> technology </option><option> theater </option><option> t-magazine </option><option> travel </option><option> upshot </option><option> us </option><option> world </option>
    </select>
    <transition>
    <div v-if="loading" class="emptyBox">
        <div class="lds-roller"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
    </div>
    <div v-else class="articleBox">
            <Item v-for="item in articles" :key="item.uri" :item = "item" @click="handleModalOpen(item)"/>
    </div>
    </transition>
    <Modal v-if="modalOpen" :item="modalItem" @close = "modalOpen = false"/>
 </main>
</template>

<script>
const API = 'https://api.nytimes.com/svc/topstories/v2/';

export default {
  name: 'App',
  data(){
    return {
      selected: 'home',
      articles: [],
      loading: true,
      modalOpen: false,
      modalItem: null,
    }
  },
  methods: {
    show(){
          this.loading = true
          axios.get(`${API}${this.selected}.json?api-key=Kof5INvpL8S7hc1CF9VVVtlBa08rYd6G`)
              .then((response) => {
                  console.log(this.selected)
                  this.articles = response.data.results
                  console.log(response.data.results)
                  this.loading = false
              })
              .catch((error) => {
                  console.log(error)
              })      
    },
    handleModalOpen(item){
      this.modalOpen = true
      this.modalItem = item

    }
  },
   beforeMount(){
    this.show()
 },
}
</script>


<style scoped>

    select{
        width: 250px;
        height: 50px;
        margin-bottom: 50px;
        border: none;
        border-bottom: 3px solid var(--color-text);
        font-size: 2em;
        background: var(--color-background);
        color: var(--color-text);
        transition: box-shadow .5s;
    }

    select:focus{
        outline: none;
        /* box-shadow: 5px 5px 20px -8px var(--color-text); */
    }
    .articleBox{
        display: grid;
        grid-gap: 20px;
        grid-template-columns: 1fr;
        transition-delay: .6s;
    }

    @media (min-width: 760px){
        select {
          width: 350px;
        }
        .articleBox{
          grid-template-columns: 1fr 1fr ;
        }
    }

    @media (min-width: 1024px){
        select {
          width: 450px;
        }
        .articleBox{
          grid-template-columns: 1fr 1fr 1fr;
            font-size: 25px;
        }
    }

    @media (min-width: 2524px){
        select {
          width: 650px;
        }
        .articleBox{
            font-size: 30px;
        }
    }

</style>