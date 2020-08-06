<template>
  <section class="hello">
    <div>
      <h2>main feature</h2>
      disini input URL::<input v-model="url" placeholder="input html disini"><br>
      disini input kata kunci::<input v-model="nonce" placeholder="input kata kunci disini"><br>
      advanced::<input type=checkbox v-model="advanced" placeholder="on atau gak"><hr>
    </div>
    <div v-if="advanced">
      <h2>Advanced feature</h2>
      pada halaman ke::<input v-model="page" placeholder="input halaman disini"><br>
      jumlah data per listing::<input v-model="datasize" placeholder="input jumlah data tampil per halaman disini"><br>
      Marking::<input type=checkbox v-model="marked" placeholder="ditandai atau tidak">
      Paginasi::<input type=checkbox v-model="paginated" placeholder="diberi paginasi atau tidak"><hr>
    </div>
    
    <article id=listing>
      <button v-on:click="getData">find!!!</button><br>
      <p v-if="message!='ok'">{{message}}</p>
      <button v-if="itemList.first != null" v-on:click="getlisting(itemList.first)">First</button>
      <button v-if="itemList.prev != null" v-on:click="getlisting(itemList.prev)">prev</button>
      <button v-if="itemList.next != null" v-on:click="getlisting(itemList.next)">next</button>
      <button v-if="itemList.last != null" v-on:click="getlisting(itemList.last)">last</button><br>
      <ul>
        <li v-for="data in itemList.data" :key="data.start">
          {{data.start}}---{{data.end}}:::{{data.text}}<br>
        </li>
      </ul>
    </article>
  </section>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      url: '',
      nonce: '',
      page: 1,
      datasize: 10,
      marked: 1,
      paginated: 1,
      advanced: false,
      message: 'ok',
      paginatednum: 1,
      markednum: 1,
      itemList: [
        {
          "data": [],
          "first": null,
          "last": null,
          "prev": null,
          "total": null,
          "page": null
        }
      ]
    }
  },
  methods: {
    validURL:function (str) {
      var pattern = new RegExp('^(https?:\\/\\/)?'+ // protocol
        '((([a-z\\d]([a-z\\d-]*[a-z\\d])*)\\.)+[a-z]{2,}|'+ // domain name
        '((\\d{1,3}\\.){3}\\d{1,3}))'+ // OR ip (v4) address
        '(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*'+ // port and path
        '(\\?[;&a-z\\d%_.~+=-]*)?'+ // query string
        '(\\#[-a-z\\d_]*)?$','i'); // fragment locator
      return !!pattern.test(str);
    },
    getData: function () {
      if(!this.validURL(this.url)){
        this.message = 'invalid URL'
      } else if (this.nonce == '') {
        this.message = 'kata kunci harus ada minimal 3 huruf'
      } else if (isNaN(this.page)) {
        this.message = 'page harus berupa angka'
      } else if (isNaN(this.datasize)) {
        this.message = 'jumlah data harus berupa angka'
      }
      else {
        if (this.paginated) this.paginatednum = 1
        else this.paginatednum = 0
        if (this.marked) this.markednum = 1
        else this.markednum = 0
        this.message = 'ok'
        axios.get('https://cari-teks-video-api.vercel.app/api/search', {
          params: {
            url: this.url,
            q: this.nonce,
            page: this.page,
            size: this.datasize,
            marked: this.markednum,
            paginated: this.paginatednum
          }
        }).then(response => {
          this.itemList = response.data
          console.log(this.itemList)
        })
      }
    },
    getlisting: function (link) {
      axios.get(link).then(response => {
        this.itemList = response.data
        console.log(this.itemList)
      }) 
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
