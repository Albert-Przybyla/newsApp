<template>
    <div class="backdrop" @click="closeModal">
        <div class="modal" :class="{ welcome: theme === 'welcome'}">
            <h2>{{header}}</h2>
            <p>{{text}}</p>
        </div>
    </div>
</template>

<script>
    export default {
    name: "App",
    props: ['header', 'text', 'theme'],

    methods: {
        closeModal(){
            this.$emit('close');
        }
    }

    }
</script>


<style scoped>
    .modal{
        width: 80%;
        padding: 20px;
        background: #222;
        border-radius: 10px; 
        text-align: center; 
        z-index: 2;
    }

    .modal.welcome {
        color: white;
        font-family: 'Courier New', Courier, monospace;
        z-index: 2;
    }

    .modal.welcome h2{
        font-size: 1.8em;
        margin-bottom: 20px;  
        z-index: 2;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
    }
</style>