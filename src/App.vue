<template>
  <main id="app">
    <Header />
    <Navbar />
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Footer />
  </main>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/navbar.vue'
import Footer from './components/footer.vue'
import Header from './components/header.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    Navbar,
    Footer,
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
  margin-top: 60px;
}
</style>
