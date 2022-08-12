<template>
    <div class="wrapper">
    <h1 class="claim">
         News by NYtimes
    </h1>
    <p class="subclaim">
        lorem ipsum
    </p>
    </div>
</template>


<style scoped>
    .wrapper{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 85%;
        font-family: 'Oswald', sans-serif;
        background-image: url('../assets/background.jpg');
        background-repeat: none;
        background-size: cover;
    }

    .claim {
        font-size: 50px;
        background: var(--color-background);
        padding: 0 10px 0 10px;
    }

    .subclaim {
        margin-top: 30px;
        font-size: 20px;
        background: var(--color-background);
        padding: 0 6px 0 6px;
    }
</style>