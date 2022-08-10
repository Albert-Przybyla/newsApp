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
            console.log('emitowanie')
        }
    }

    }
</script>


<style scoped>
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: #222;
        border-radius: 10px; 
        text-align: center;   
    }

    .modal.welcome {
        color: white;
        font-family: 'Courier New', Courier, monospace;
    }

    .modal.welcome h2{
        font-size: 1.8em;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }
</style>