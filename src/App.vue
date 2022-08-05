<script setup>
 import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">news</RouterLink>
        <RouterLink to="/search">search</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
  <RouterView />
</template>
<script>

export default {
  name: 'App',
  data(){
    return {
      title: "dsdas"
    }
  }

}
</script>

<style scoped>



@media (min-width: 1024px) {

}
</style>
