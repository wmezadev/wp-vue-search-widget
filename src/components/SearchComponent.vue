<template>
  <section class="container">
    <div class="row">
        <div class="col col-md-4">
          <input class="form-control" type="text" name="search" placeholder="Búsqueda">
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
                  <div class="col-xs-12 col-sm-6 col-md-4">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" src="https://sunlimetech.com/portfolio/boot4menu/assets/imgs/team/img_01.png" alt="card image"></p>
                                          <h4 class="card-title">Sunlimetech</h4>
                                          <p class="card-text">This is basic card with image on top, title, description and button. asdsadsadasdsasa asdsadsadsa asdsa</p>
                                          <a href="#" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <!-- ./individual search result -->
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" src="https://sunlimetech.com/portfolio/boot4menu/assets/imgs/team/img_02.png" alt="card image"></p>
                                          <h4 class="card-title">Sunlimetech</h4>
                                          <p class="card-text">This is basic card with image on top, title, description and button.</p>
                                          <a href="#" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <!-- ./individual search result -->
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" src="https://sunlimetech.com/portfolio/boot4menu/assets/imgs/team/img_03.png" alt="card image"></p>
                                          <h4 class="card-title">Sunlimetech</h4>
                                          <p class="card-text">This is basic card with image on top, title, description and button.</p>
                                          <a href="#" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <!-- ./individual search result -->
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" src="https://sunlimetech.com/portfolio/boot4menu/assets/imgs/team/img_04.jpg" alt="card image"></p>
                                          <h4 class="card-title">Sunlimetech</h4>
                                          <p class="card-text">This is basic card with image on top, title, description and button.</p>
                                          <a href="#" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <!-- ./individual search result -->
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" src="https://sunlimetech.com/portfolio/boot4menu/assets/imgs/team/img_05.png" alt="card image"></p>
                                          <h4 class="card-title">Sunlimetech</h4>
                                          <p class="card-text">This is basic card with image on top, title, description and button.</p>
                                          <a href="#" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                  <!-- ./individual search result -->
                  <!-- individual search result -->
                  <div class="col-xs-12 col-sm-6 col-md-4">
                      <div class="image-flip">
                          <div class="mainflip">
                              <div class="frontside">
                                  <div class="card">
                                      <div class="card-body text-center">
                                          <p><img class=" img-fluid" src="https://sunlimetech.com/portfolio/boot4menu/assets/imgs/team/img_06.jpg" alt="card image"></p>
                                          <h4 class="card-title">Sunlimetech</h4>
                                          <p class="card-text">This is basic card with image on top, title, description and button.</p>
                                          <a href="#" class="btn btn-primary btn-md">Descargar <i class="fa fa-download"></i></a>
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

export default {
  name: 'search-component',
  props: {
    query: String
  },
  data: function () {
    return { 
        
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
