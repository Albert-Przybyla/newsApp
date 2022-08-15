<template>

    <div class="item" :style="style">

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
    computed: {
      style () {
        return 'background-image: url(' +  this.item.multimedia[1].url + ');'
      }
    },
}
</script>


<style scoped>
    .item{
        width: 300px;
        min-height: 300px;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
    }

    .item h2{
        margin: 10px 0 10px 0;
    }

    .item p{
        margin: 0 5px 5px 5px;
    }


    .item i {
        margin: 5px 0 10px 0;
        width: 100%;
        text-align: right;
    }

</style>