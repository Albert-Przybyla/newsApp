<template>

    <div class="item">
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
}
</script>


<style scoped>
    .item{
        width: 300px;
        min-height: 300px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        border-bottom: 1px solid var(--color-text);
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