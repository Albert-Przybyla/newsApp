<template>

    <div 
    class="item" 
    :style="style" 
    @mouseover="show=true" 
    @mouseleave="show=false"
    >
        <div v-if="show" class="title">
            <p>{{item.title}}</p>
        </div>
        <div class="titleMini">
            <p>{{item.title}}</p>
        </div>
    </div>

</template>

<script>
export default {
  name: "homeItem",
    props: {
        item:{
            type: Object,
            required: true,
        }
    },
    data(){
        return{
            show: false
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
    .item{
        width: 80vw;
        height: 80vw;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
    }

    .title {
        display: none;
    }

    .titleMini{
        margin-top: 60%;
        width: 100%;
        height: 40%;
        background-color: var(--color-background);
        opacity: 0.9;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        font-size: 15px;
    }

    @media (min-width: 760px){
        .item{
            width: 40vw;
            height: 40vw;
        }
    }

    @media (min-width: 1024px){
        .titleMini{
            display: none;
        }

        .item{
            width: 25vw;
            height: 25vw;
        }

        .title{
        width: 100%;
        height: 100%;
        background-color: var(--color-background);
        opacity: 0.9;
        display: flex;
        justify-content: center;
        align-items: center;
        }

        .title p{
        width: 60%;
        font-size: 30px;
        text-align: center;
        }
    }

</style>