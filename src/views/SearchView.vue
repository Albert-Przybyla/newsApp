<script setup>
import axios from 'axios';
import debounce from 'https://unpkg.com/vue-debounce@3.0.2/dist/debounce.min.mjs';
</script>

<template>
<main>
    <div id="search">
        <input
        type="text"
        name="search"
        placeholder="np. Ukraine"
        v-model="searchValue"
        @input="handleInput"
        />
    </div>
    <div v-if="searchValue.length>0" class="articleBox">
            <div v-for="article in articles" :key="article._id" class="articleItem">
                <h3>{{article.headline.main}}</h3>
                <p>{{article.load_paragraph}}</p>
            </div>
        </div>
    <div v-else class="articleBox">
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

    #search{
        display: flex;
        flex-direction: column;
        width: 250px;
        height: 20vh;
    }

    input{
        height: 50px;
        border: none;
        border-bottom: 3px solid var(--color-text);
        font-size: 2em;
        background: var(--color-background);
        color: white;
        transition: box-shadow .5s;
    }

    input:focus{
        outline: none;
        /* box-shadow: 5px 5px 20px -8px var(--color-text); */
    }

    .articleBox{
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }

    @media (min-width: 760px){
        #search{
            width: 350px;
        }

        .articleBox{
            font-size: 25px;
        }
    }

    @media (min-width: 1024px){
        #search{
            width: 400px;
        }

        .articleBox{
            font-size: 25px;
        }
    }

    @media (min-width: 2524px){
        #search{
            margin-top: 50px;
            width: 650px;
        }
        .articleBox{
            font-size: 30px;
        }
    }

</style>
