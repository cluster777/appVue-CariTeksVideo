<template>
  <main id="app">
    <Header />
    <HelloWorld msg="Welcome to Your Vue.js App"/>

  </main>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

import Header from './components/header.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    Header
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
  background-color: #2b2b2b;
  height: 100vh;
}
</style>
