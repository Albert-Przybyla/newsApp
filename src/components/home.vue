<script setup>
    import claim from "./claim.vue"
    import Headerc from "./Headerc.vue"
</script>

<template>
    <header>
    <claim/>

      <Headerc :sticky="sticky === true"/>
    </header>
</template>

<script>
export default {
  name: "App",
  data(){
    return {
        sticky: false
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll(event) {
        if(scrollY>=screen.height * 0.85){
            this.sticky = true
        }else{
            this.sticky = false
        }
    },
  },
};
</script>

<style scoped>
    header {
        height: 100vh;
        width: 100%;
    }
</style>