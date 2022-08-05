<script setup>

</script>

<template>
  <main>

  </main>
</template>

<script>
export default {
    name: 'App',
        date() {
        return {
            searchValue: '',
        }
    },
    Methods: {
        handleInput(){
            console.log(searchValue)
        }
    }
}

</script>
