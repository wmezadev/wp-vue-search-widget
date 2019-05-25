<template>
  <section class="container">
    <div class="row">
        <div class="col col-md-4">
          <input class="form-control" v-model="search"  type="text" name="search" placeholder="Búsqueda">
        </div>
        <div class="col col-md-4">
          <select class="form-control" name="category">
            <option value=""> Una opción </option>
          </select>
        </div>
        <div class="col col-md-4">
          <button class="btn btn-primary">Buscar</button>
        </div>
    </div>
    <div class="row">
      <section id="results" class="pb-5">
          <div class="container display-flex">
              <h3>Resultados</h3>
              <div class="row">
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4" v-for="(post, index) in filteredList" v-bind:key="index">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" v-bind:src="post.img" alt="card image"></p>
                                          <h4 class="card-title">{{ post.title }}</h4>
                                          <p class="card-text">{{ post.author }}</p>
                                          <a v-bind:href="post.link" target="_blank" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
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
class Post {
  constructor(title, link, author, img) {
    this.title = title;
    this.link = link;
    this.author = author;
    this.img = img;
  }
}
export default {
  name: 'search-component',
  props: {
    query: String
  },
  data: function () {
    return { 
        search: '',
        postList : [
          new Post(
            'Vue.js', 
            'https://vuejs.org/', 
            'Chris', 
            'https://vuejs.org//images/logo.png'
          ),
          new Post(
            'React.js', 
            'https://facebook.github.io/react/', 
            'Tim',
            'https://daynin.github.io/clojurescript-presentation/img/react-logo.png'
          ),
          new Post(
            'Angular.js', 
            'https://angularjs.org/', 
            'Sam', 
            'https://angularjs.org/img/ng-logo.png'
          ),
          new Post(
            'Ember.js', 
            'http://emberjs.com/', 
            'Rachel',
            'http://www.gravatar.com/avatar/0cf15665a9146ba852bf042b0652780a?s=200'
          ),
          new Post(
            'Meteor.js', 
            'https://www.meteor.com/', 
            'Chris', 
            'http://hacktivist.in/introduction-to-nodejs-mongodb-meteor/img/meteor.png'
          ),
          new Post(
            'Aurelia', 
            'http://aurelia.io/', 
            'Tim',
            'https://cdn.auth0.com/blog/aurelia-logo.png'
          ),
          new Post(
            'Node.js', 
            'https://nodejs.org/en/', 
            'A. A. Ron',
            'https://code-maven.com/img/node.png'
          ),
          new Post(
            'Pusher', 
            'https://pusher.com/', 
            'Alex', 
            'https://avatars1.githubusercontent.com/u/739550?v=3&s=400'
          ),
          new Post(
            'Feathers.js', 
            'http://feathersjs.com/', 
            'Chuck',
            'https://cdn.worldvectorlogo.com/logos/feathersjs.svg'
          )
        ]
      }
  },
  computed: {
    filteredList() {
      return this.postList.filter(post => {
        return post.title.toLowerCase().includes(this.search.toLowerCase())
      })
    }
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


.frontside .card,
.backside .card {
    min-height: 312px;
}

.backside .card a {
    font-size: 18px;
    color: #e36334 !important;
}

.frontside .card .card-title,
.backside .card .card-title {
    color: #e36334 !important;
}

.frontside .card .card-body img {
    width: 120px;
    height: 120px;
}
</style>
