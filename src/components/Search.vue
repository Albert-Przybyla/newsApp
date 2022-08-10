<script setup>
import axios from 'axios';
import debounce from 'https://unpkg.com/vue-debounce@3.0.2/dist/debounce.min.mjs';
</script>

<template>
<div class="wrapper">
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
        <ul>
            <li v-for="item in resaults" :key="item">
                <p>{{item.web_url}}</p>
                <p>lala</p>
            </li>
        </ul>
</div>
</template>

<script>
const API = 'https://api.nytimes.com/svc/search/v2/articlesearch.json';

export default{
    date(){
        return{
            searchValue: '',
            resaults: [],
        }
    },
    methods: {
        handleInput: debounce(function() {
            axios.get(`${API}?q=${this.searchValue}&api-key=Kof5INvpL8S7hc1CF9VVVtlBa08rYd6G`)
                .then((response) => {
                    this.resaults = response.data.response.docs
                    console.log(response.data.response.docs)
                    // console.log(this.searchValue)
                })
                .catch((error) => {
                    console.log(error)
                })
        }, 1000),
    },

}

</script>


<style scoped>
    .wrapper{
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
        padding: 30px;
        width: 100%;
    }

    .search{
        display: flex;
        flex-direction: column;
        width: 30%;
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

</style>