<script setup>
import axios from 'axios';
import debounce from 'https://unpkg.com/vue-debounce@3.0.2/dist/debounce.min.mjs';
import Item from '@/components/Item.vue';
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
    <transition>
    <div v-if="!searchValue" class="emptyBox">
        <p>type something to find the article</p>
    </div>
        <div v-else-if="searchValue && loading" class="emptyBox">
        <div class="lds-roller"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
    </div>
    <div v-else-if="searchValue && !loading" class="articleBox">
        <Item v-for="item in articles" :key="item._id" :web = "item.web_url" :headLine = "item.headline.main" :content = "item.lead_paragraph" :author = "item.byline.original"/>
    </div>

    </transition>
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
        loading: false,
    }
  },
  methods: {
            handleInput: debounce(function() {
            this.loading = true;
            axios.get(`${API}?q=${this.searchValue}&api-key=Kof5INvpL8S7hc1CF9VVVtlBa08rYd6G`)
                .then((response) => {
                    this.articles = response.data.response.docs
                    console.log(response.data.response.docs)
                    this.loading = false;
                })
                .catch((error) => {
                    console.log(error)
                })
        }, 1000)
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
        color: var(--color-text);
        transition: box-shadow .5s;
    }

    input:focus{
        outline: none;
        /* box-shadow: 5px 5px 20px -8px var(--color-text); */
    }

    .articleBox{
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
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
            grid-template-columns: 1fr 1fr;
            display: grid;
            width: 100%;
            grid-template-columns: 1fr;
            grid-gap: 6vw;
        }
    }

    @media (min-width: 2524px){
        #search{
            margin-top: 50px;
            width: 650px;
        }
        .articleBox{
            font-size: 30px;
            grid-template-columns: 1fr 1fr 1fr;
        }
    }

</style>
