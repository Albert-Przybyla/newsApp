<script setup>
 import News from "@/components/News.vue"
</script>

<template>
  <main>
    <News/>
  </main>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      components: { News },
    }
  }
}
</script>
