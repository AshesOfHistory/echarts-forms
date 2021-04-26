<template>
  <div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <RandomExcel></RandomExcel>
  </div>
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import RandomExcel from './components/randomExcel'

export default {
  name: 'App',
  components: {
    HelloWorld,
    RandomExcel
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
  margin-top: 60px;
}
</style>
