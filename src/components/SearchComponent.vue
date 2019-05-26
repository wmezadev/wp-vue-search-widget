<template>
  <section class="container">
    <div class="row">
      <section id="results" class="pb-5">
          <div class="container display-flex">
              <div class="row">
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
                  <form class="form-inline" id="search-form" @submit="searchPosts">
                    <div class="form-group">
                      <label class="sr-only" for="search">Ingrese el título</label>
                      <input class="form-control" v-model="search"  type="text" name="search" id="search" placeholder="Búsqueda por titulo">
                    </div>
                    <div class="form-group">
                      <label class="sr-only" for="category"> Seleccione una categoría</label>
                      <select class="form-control" name="category" id="category" v-model="category">
                        <option value="" selected>  -- seleccionar categoría -- </option>
                        <option v-for="category in categories" v-bind:key="category.id" v-bind:value="category.id">{{category.name}}</option>
                      </select>
                    </div>
                      <button class="btn btn-md btn-primary" type="submit">Buscar</button>
                  </form>
                </div>
              </div>
              <div class="row">
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4" v-for="(post, index) in filteredPosts" v-bind:key="index">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" v-bind:src="post.fimg_url" alt="card image"></p>
                                          <h4 class="card-title">{{ post.title.rendered }}</h4>
                                          <p class="card-text">{{ post.description }}</p>
                                          <a v-bind:href="post.download_url" target="_blank" class="btn btn-primary btn-md" download>Descargar <i class="fa fa-download"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
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
        search: '',
        posts: [],
        filteredPosts: [],
        categories: [],
        category: null
      }
  },
  methods: {
    searchPosts: function (e){
      e.preventDefault()
      let filtered_posts = []
      filtered_posts = this.posts.filter(post => {
        return post.title.rendered.toLowerCase().includes(this.search.toLowerCase())
      })
      if(this.category){
        filtered_posts = filtered_posts.filter(post => {
          return post.categoria_libro.find(categoria => {
              return parseInt(categoria) === parseInt(this.category)
            })
        })
      }
      this.filteredPosts = filtered_posts
    },
    getList: function () {
      axios.get('http://www.mujeresdeoro.co/wp-json/wp/v2/books?per_page=6&order=desc')
        .then((response) => {
          this.posts= this.filteredPosts = response.data
           // eslint-disable-next-line 
          console.log(response.data)
        })
    },
    getCategories: function () {
      axios.get('http://www.mujeresdeoro.co/wp-json/wp/v2/categoria_libro?context=embed')
        .then((response) => {
          this.categories = response.data
        })
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
    background: #eee !important;
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
    background: #ffffff;
    padding: 10%;
    margin: 10% 5%;
}


.frontside .card .card-title,
.backside .card .card-title {
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
</style>
