<script>
export default{
    date(){
        return{
            searchValue: 'ss',
            count: 0
        }
    },
    methods: {
        handleInput(){
            console.log(this.searchValue)
        }
    } 

}

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
</div>
</template>


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