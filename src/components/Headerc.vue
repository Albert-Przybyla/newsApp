<template>
      <nav :class="{sticky}" id="nav">
        <RouterLink to="/">news</RouterLink>
        <RouterLink to="/search">search</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
</template>

<script>
    export default {
    name: "App",
    props: {
      sticky: {
        type: Boolean,
        default: false
      }
    }
    }
</script>

<style scoped>
  nav{
  width: 100%;
  height: 15%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  font-size: 2em;
  z-index: 1;
  background: var(--vt-c-black);
  transition: .2s ease-out;
}

.sticky{
  position: fixed;
  top: 0;
  left: 0;
  height: 8vh;
}

@media (min-width: 760px) {
  nav{
  font-size: 40px;
  }
}

@media (min-width: 1024px) {
  nav{
  font-size: 40px;
  }
}

@media (min-width: 2524px){
  nav{
  font-size: 50px;
  height: 10%;
  }
}

</style>
