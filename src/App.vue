<template>
  <div id="app">
    <navbar />
    <div id="main">
      <router-view/>
    </div>
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
  color: #2c3e50;
}
#main {
  padding: 2rem 8rem 2rem 8rem;
  min-height: calc(100vh - 4.5rem - 5.25rem);
}
</style>
