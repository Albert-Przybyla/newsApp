<script setup>
import Search from '@/components/search.vue'
</script>

<template>
    <Search/>
</template>

<script>
export default {
  name: 'search',
  data(){
    return {
      components: { Search },
    }
  }

}
</script>