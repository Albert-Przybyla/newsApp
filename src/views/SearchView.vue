<script setup>
import axios from 'axios';
import debounce from 'https://unpkg.com/vue-debounce@3.0.2/dist/debounce.min.mjs';
</script>

<template>
<main>
    <div class="search">
        <label for="search">Search:</label>
        <input
        type="text"
        name="search"
        placeholder="np. Biden"
        v-model="searchValue"
        @input="handleInput"
        />
    </div>
    <div v-if="searchValue.length>0" class="searchContent">
        <ul>
            <li v-for="article in articles" :key="article._id">
                <a href="{{article.web_url}}">{{article.headline.main}}</a>
            </li>

        </ul>
        </div>
    <div v-else class="searchContent">
        <p>type something to find the article</p>
    </div>
</main>
</template>

<script>
const API = 'https://api.nytimes.com/svc/search/v2/articlesearch.json';

export default {
  name: 'App',
  data(){
    return {
        searchValue: '',
        articles: [],
    }
  },
  methods: {
            handleInput: debounce(function() {
            axios.get(`${API}?q=${this.searchValue}&api-key=Kof5INvpL8S7hc1CF9VVVtlBa08rYd6G`)
                .then((response) => {
                    this.articles = response.data.response.docs
                    console.log(response.data.response.docs)
                })
                .catch((error) => {
                    console.log(error)
                })
        }, 500)
  }
}
</script>

<style scoped>

    .search{
        display: flex;
        flex-direction: column;
        width: 80%;
        height: 20vh;
    }

    input{
        height: 50px;
        border: none;
        border-bottom: 3px solid black;
        font-size: 2em;
        background: var(--color-background);
        color: white;
    }

    input:focus{
        border: none;
        border-bottom: 3px solid black;
    }

    label {
        font-family: Montserrat, sans-serif;
    }

    .searchContent{
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }

</style>
