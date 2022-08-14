<script setup>
import axios from 'axios';
import Item from '@/components/Item.vue';
</script>

<template>
  <main>
    <select
    v-model="selected"
    @input="show">
      <option default>home</option><option> arts </option><option> automobiles </option><option> books </option><option> business </option><option> fashion </option><option> food </option><option> health </option><option> home </option><option> insider </option><option> magazine </option><option> movies </option><option> nyregion </option><option> obituaries </option><option> opinion </option><option> politics </option><option> realestate </option><option> science </option><option> sports </option><option> sundayreview </option><option> technology </option><option> theater </option><option> t-magazine </option><option> travel </option><option> upshot </option><option> us </option><option> world </option>
    </select>
    <div class="articleBox">
            <Item v-for="item in articles" :key="item.uri" :web = "item.url" :headLine = "item.title" :content = "item.abstract" :author = "item.byline"/>
            <!-- <div v-for="item in articles" :key="item.uri" class="articleItem">
              ls
            </div> -->
    </div>
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
    }
  },
  methods: {
    show(){
          axios.get(`${API}${this.selected}.json?api-key=Kof5INvpL8S7hc1CF9VVVtlBa08rYd6G`)
              .then((response) => {
                  this.articles = response.data.results
                  // console.log(response.data.results[0].multimedia[0].url)
              })
              .catch((error) => {
                  console.log(error)
              })      
    }
  },
   beforeMount(){
    this.show()
 },
}
</script>


<style scoped>
    .articleBox{
        display: grid;
        width: 100%;
        grid-template-columns: 1fr;
        grid-gap: 6vw;
    }

    @media (min-width: 1024px){

        .articleBox{
            font-size: 25px;
            grid-template-columns: 1fr 1fr;
        }
    }

    @media (min-width: 2524px){
        .articleBox{
            font-size: 30px;
            grid-template-columns: 1fr 1fr 1fr;
        }
    }

</style>