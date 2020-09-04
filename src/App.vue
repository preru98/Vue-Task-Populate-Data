<template>
  <div id="app">
    <PopulateData/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import PopulateData from './components/PopulateData'

export default {
  name: 'App',
  components: {
    HelloWorld,
    PopulateData
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
