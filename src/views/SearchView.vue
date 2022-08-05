<template>
<div class="wrapper">
    <div class="search">
        <label for="search">Search:</label>
        <input 
        type="text" 
        id="search" 
        name="search"
        placeholder="np. Biden"
        />  
    </div>
</div>
</template>

<script>


</script>

<style lang="css" scoped>
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