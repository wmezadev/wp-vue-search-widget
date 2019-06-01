<template>
  <section class="container">
    <div class="row">
      <section id="results" class="pb-5 display-flex">
          <div class="container">
              <div class="row">
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
                  <form class="form-inline" id="search-form" @submit.prevent="getList">
                    <div class="form-group">
                      <label class="sr-only" for="search">Buscar</label>
                      <input class="form-control" v-model="search"  type="text" name="search" id="search" placeholder="Búsqueda">
                    </div>
                    <div class="form-group">
                      <label class="sr-only" for="category"> Seleccione una categoría</label>
                      <select class="form-control" name="category" id="category" v-model="category">
                        <option value="" selected>  -- todas las categorías -- </option>
                        <option v-for="category in categories" v-bind:key="category.id" v-bind:value="category.id">{{category.name}}</option>
                      </select>
                    </div>
                      <button class="btn btn-md btn-primary" type="submit">Buscar</button>
                  </form>
                </div>
              </div>
              <div class="row">
                  <!-- individual search result -->
                  <div div class="col-md-12" style="align-items: center;justify-content: center;margin-top: 10rem;" v-if="loading">
                    <div class="lds-grid"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
                  </div>
                  <div class="col-xs-12 col-sm-6 col-md-4" v-else v-for="(post, index) in posts" v-bind:key="index">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" v-bind:src="post.fimg_url" alt="card image"></p>
                                          <h4 class="card-title">{{ post.title.rendered }}</h4>
                                          <p class="card-text">{{ post.description }}</p>
                                          <a v-if="post.url_type === 'download'" v-bind:href="post.download_url" target="_blank" class="btn btn-primary btn-md" download>Descargar <i class="fa fa-download"></i></a>
                                          <a v-else v-bind:href="post.download_url" target="_blank" class="btn btn-primary btn-md">Abrir <i class="fa fa-link"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <div class="col-md-12" style="align-items: center;justify-content: center;margin-top: 2rem;"  v-if="pages>1">
                    <ul class="pagination">
                      <li v-for="n in parseInt(pages)" v-bind:key="parseInt(n)" :class="n === currentPage ? 'disabled' : ''"><a href="#!" @click="paginate(n)">{{n}}</a></li>
                    </ul>
                  </div>
                  <!-- ./individual search result -->
              </div>
          </div>
      </section>
    </div>
    <!-- results -->
  </section>
</template>

<script>
import axios from 'axios'

export default {
  name: 'search-component',
  props: {
    query: String
  },
  data: function () {
    return { 
        loading: true,
        search: '',
        posts: [],
        categories: [],
        category: '',
        pages: 1,
        currentPage: 1,
      }
  },
  computed: {
    searchURI: function () {
      return encodeURI(this.search)
    }
  },
  methods: {
    getList: function () {
      this.loading = true
      axios.get(`http://www.mujeresdeoro.co/wp-json/wp/v2/books?per_page=9&order=desc&search=${this.searchURI}&categoria_libro=${this.category}&page=${this.currentPage}`)
        .then((response) => {
          this.posts = response.data
          this.pages = response.headers['x-wp-totalpages']
          this.loading = false
        })
    },
    getCategories: function () {
      axios.get('http://www.mujeresdeoro.co/wp-json/wp/v2/categoria_libro?context=embed')
        .then((response) => {
          this.categories = response.data
        })
    },
    paginate: function(n) {
      this.currentPage = n
      this.getList()
    }
  },
  mounted: function (){
    this.getCategories()
    this.getList()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
@import url("https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css");
@import url('https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');
#results {
    background: #ffffff !important;
}

.display-flex .row{
  display: flex;
  flex-wrap: wrap;
}
.display-flex .row > [class*='col-'] {
  display: flex;
  flex-direction: column;
}

.btn-primary:hover,
.btn-primary:focus {
    color: #e36334;
    background-color: #ffffff;
    border: 1px solid #e36334;
    box-shadow: none;
    outline: none;
}

.btn-primary {
    color: #fff;
    background-color: #e36334;
    border-color: #e36334;
    border-radius: 0%;
}

section {
    padding: 60px 0;
}

section .section-title {
    text-align: center;
    color: #e36334;
    margin-bottom: 50px;
    text-transform: uppercase;
}

#results .card {
    border: none;
    background: #f5f5f5;
    padding: 10%;
    margin: 10% 5%;
}

.card-body {
    height: 300px;
}
.frontside .card .card-title{
    color: #e36334 !important;
}
.frontside .card .card-body img {
    width: 120px;
    height: 120px;
}
@media only screen and (min-width: 700px) {
#search-form .form-group {
  margin-right: 10px;
}
}

.pagination>li>a, .pagination>li>span {
  color:#e36334;
}
.pagination>li>a:focus, .pagination>li>a:hover, .pagination>li>span:focus, .pagination>li>span:hover{
  color:#973a18;
}

/*
 * Pure CSS Spinner 
*/
.lds-grid {
  display: inline-block;
  position: relative;
  width: 64px;
  height: 64px;
}
.lds-grid div {
  position: absolute;
  width: 13px;
  height: 13px;
  border-radius: 50%;
  background: #cccccc;
  animation: lds-grid 1.2s linear infinite;
}
.lds-grid div:nth-child(1) {
  top: 6px;
  left: 6px;
  animation-delay: 0s;
}
.lds-grid div:nth-child(2) {
  top: 6px;
  left: 26px;
  animation-delay: -0.4s;
}
.lds-grid div:nth-child(3) {
  top: 6px;
  left: 45px;
  animation-delay: -0.8s;
}
.lds-grid div:nth-child(4) {
  top: 26px;
  left: 6px;
  animation-delay: -0.4s;
}
.lds-grid div:nth-child(5) {
  top: 26px;
  left: 26px;
  animation-delay: -0.8s;
}
.lds-grid div:nth-child(6) {
  top: 26px;
  left: 45px;
  animation-delay: -1.2s;
}
.lds-grid div:nth-child(7) {
  top: 45px;
  left: 6px;
  animation-delay: -0.8s;
}
.lds-grid div:nth-child(8) {
  top: 45px;
  left: 26px;
  animation-delay: -1.2s;
}
.lds-grid div:nth-child(9) {
  top: 45px;
  left: 45px;
  animation-delay: -1.6s;
}
@keyframes lds-grid {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

</style>
