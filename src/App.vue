<template>
  <div id="app">
    <h1 class="Ship_Title">Ships</h1>
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.Ship_Title {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #42b983;
  text-align: center;
}
</style>
