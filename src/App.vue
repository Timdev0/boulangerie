<template>
  <div id="app">
    <navbar />
    <router-view/>
    <footbar />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Footbar from './components/Footbar.vue'

export default {
  components: {
    Navbar,
    Footbar
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
