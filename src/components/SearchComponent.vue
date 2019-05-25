<template>
    <div class="row">
        <div class="col col-md-4">
          <label class="form-control"> Buscar </label>
          <input type="text" name="search" placeholder="Búsqueda">
        </div>
        <div class="col col-md-4">
          <label class="form-control"> Categoria </label>
          <select name="category">
            <option value=""> Una opción </option>
          </select>
        </div>
        <div class="col col-md-4">
          <button class="btn btn-primary">Buscar</button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'search-component',
  props: {
    query: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
