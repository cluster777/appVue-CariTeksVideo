<template>
  <section class="footer">
    <h1>FOOTER</h1>

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
.footer {
  width: 100%;
  background-color: #5f5f5f;
  color: white;
  text-align: center;

}
.footer h1 {
  float: left;
  color: #42b983;
  text-align: center;
  text-decoration: none;
  font-size: 18px; 
}
.footer h6 {
  float: right;
  color: #42b983;
  text-align: center;
  text-decoration: none;
}

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
