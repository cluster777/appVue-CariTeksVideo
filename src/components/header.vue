<template>
  <section class="header">
    <h1>HEADER</h1>

    <h6>&copy; david Laksmana 2020</h6>

  </section>
</template>

<script>

export default {
  nama: ''
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
.header {
  overflow: hidden;
  background-color: #5f5f5f;
  width: 100%;
}
.header h1 {
  float: left;
  color: #42b983;
  text-align: center;
  text-decoration: none;
  font-size: 18px; 
}
.header h6 {
  float: right;
  color: #42b983;
  text-align: center;
  text-decoration: none;
}

li {
  display: inline-block;
  margin: 0 10px;
}

</style>
