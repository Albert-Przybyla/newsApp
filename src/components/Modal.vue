<template>
    <div class="backdrop">
        <div class="modal">
           <div class="photo" :style="style">
                
                </div>
           <div class="content">
            <div class="article">
                <h2 class="title">
                    {{item.title}}
                </h2>
                <p class="text">
                    {{item.abstract}}
                </p>
                <p class="text">
                <i>by {{item.byline}}</i>
                </p>
            </div>
                <a :href="item.url" class="modalLink">full article anvible here</a>
           </div>
           <div class="close" @click="closeModal">

           </div>
        </div>
    </div>
</template>

<script>
    export default {
    name: "App",
    props: {
        item:{
            type: Object,
            required: true,
        }
    },
    methods: {
        closeModal(){
            this.$emit('close');
        }
    },
    computed: {
      style () {
        return 'background-image: url(' +  this.item.multimedia[1].url + ');'
      }
    },

    }
</script>


<style scoped>

    .backdrop{
        width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 5;
    }

    .modal{
        display: flex;
        flex-direction: column;
        width: 100%;
        height: 100%;
        padding: 50px;
        justify-content: center;
        align-items: center;
        background-color: var(--color-background);
    }
    .article{
        overflow: scroll;
    }

    .content{
        display: flex;
        flex-direction: column;
        height: 50%;
        width: 100%;
    }

    .photo {
        width: 95%;
        height: 60%;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
        margin-bottom: 10px;
    }

    .title{
        margin-bottom: 15px;
    }

    .text{
        margin-bottom: 10px;
    }

    .modalLink{
        font-size: 25px;
        text-align: right;
        width: 100%;
    }

    .close {
        position: absolute;
        width: 30px;
        height: 30px;
        padding: 30px;
        right: 0;
        top: 0;
        cursor: pointer;
    }

    .close::before, .close::after {
            position: absolute;
            top: 30px;
            right: 20px;
            content: '';
            width: 20px;
            height: 2px;
            background: var(--color-text);
            display: block;
}
    .close::before{
        transform: rotate(45deg);
    }

    .close::after{
        transform: rotate(-45deg);
    }


@media (min-width: 1024px){
    .modal{
        overflow: hidden;
        width: 70%;
        height: 60%;
        padding: 20px;
        background: var(--color-background);
        text-align: center; 
        box-shadow: 0 30px 30px -10px rgba(0,0,0,0.3);
        flex-direction: row;
        justify-content: space-around;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.3);
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
    }

    .article{
        overflow: hidden;
    }

    .photo{
        width:60%;
        height: 90%;
    }

    .content{
        height: 100%;
        width: 30%;
        justify-content: space-around;
    }

}
</style>