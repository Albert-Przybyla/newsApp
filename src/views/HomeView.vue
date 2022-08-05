<script setup>
 import Test from "@/components/Test.vue"
</script>

<template>
  <main>
    <Test/>
  </main>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      components: { Test },
    }
  }
}
</script>
