<script>
export default {
  data() {
    return {
      count: 0,
      utl: "https://api.nytimes.com/svc/topstories/v2/world.json?api-key=Kof5INvpL8S7hc1CF9VVVtlBa08rYd6G",

    }
  }
}

</script>

<template>
  <!-- <button @click="count++">You clicked me {{ count }} times.</button> -->
  <div id="articles"></div>
</template>