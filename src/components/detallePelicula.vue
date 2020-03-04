<template>
    <div>
        <b-card
        :title="datosPelicula.Title"
        :img-src="datosPelicula.Poster"
        img-left
        class="mb-3"
        tag="article"
        >
        <b-card-text>
          <h2> {{datosPelicula.Year}}</h2>
          {{datosPelicula.Plot}}
          <br>
           <b-badge v-for="genero in datosPelicula.Genre.split(',')" :key="genero.Title" variant="primary">{{genero}}</b-badge>
        </b-card-text>
        </b-card>
    </div>
</template>
<script>

export default {
  data () {
    return {

    }
  },
  props: {
    datosPelicula: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
