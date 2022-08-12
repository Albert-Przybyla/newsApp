<script setup>
import axios from 'axios';
</script>

<template>
  <main>
    <select
    v-model="selected"
    @input="show">
      <option default>home</option><option> arts </option><option> automobiles </option><option> books </option><option> business </option><option> fashion </option><option> food </option><option> health </option><option> home </option><option> insider </option><option> magazine </option><option> movies </option><option> nyregion </option><option> obituaries </option><option> opinion </option><option> politics </option><option> realestate </option><option> science </option><option> sports </option><option> sundayreview </option><option> technology </option><option> theater </option><option> t-magazine </option><option> travel </option><option> upshot </option><option> us </option><option> world </option>
    </select>
    {{selected}}
    <ul>
            <li v-for="article in articles" :key="article.uri">
                <a href="#">{{article.title}}</a>
            </li>
    </ul>
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
                  console.log(response)
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
