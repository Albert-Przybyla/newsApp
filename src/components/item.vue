<template>

    <div class="item" >
        <h2>{{headLine}}</h2>
        <p>{{content}}</p>
        <a :href="web">full article available here</a>
        <i>by: {{author}}</i>
    </div>

</template>

<script>
export default {
  name: "item",
    props: ['web', 'headLine', 'content', 'author' , 'photo'],
}
</script>


<style scoped>
    .item{
        width: 80vw;
        min-height: 40vw;
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