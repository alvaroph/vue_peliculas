<template>
  <div class="main">
    <b-container class="bv-example-row">
    <b-row>
      <b-col cols="1"></b-col>
      <b-col cols="10">
        <b-form inline>
        <label class="sr-only" for="inline-form-input-name">Película</label>
           <b-input
              v-model="query"
              id="inline-form-input-name"
              class="mb-2 mr-sm-2 mb-sm-0"
              placeholder="Jane Doe"
            ></b-input>
            <b-button @click="hazQuery" variant="primary">Buscar</b-button>
            <b-button @click="ordenarAnyo" variant="primary">Ordenar</b-button>
          </b-form>
           <b-row v-show="verDetalle">
              <b-button @click="verDetalle=false" variant="primary">Cerrar</b-button>
              <detallePelicula  :datosPelicula=detailedResults></detallePelicula>
          </b-row>

          <b-row>
            <b-col cols="4"  v-for="actual in results.Search" :key="actual.imdbID">
              <fichaPelicula @verDetalle="peticionDetalle" :movie=actual></fichaPelicula>
            </b-col>
          </b-row>
        </b-col>
        <b-col cols="1"></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

import detallePelicula from '@/components/detallePelicula.vue'
import fichaPelicula from '@/components/fichaPelicula.vue'
import axios from 'axios'

export default {
  data () {
    return {
      query: '',
      results: [],
      verDetalle: 'false',
      detailedResults: ''
    }
  },
  methods: {
    peticionDetalle: function (data) {
      axios.get(`http://www.omdbapi.com/?apikey=19f8a30e&i=${data}`).then(response => { this.detailedResults = response.data; console.log(response) })
      console.log('me lleg ala peticion' + data)
      this.verDetalle = true
    },
    hazQuery: function () {
      axios.get(`http://www.omdbapi.com/?apikey=19f8a30e&s=${this.query}`).then(response => { this.results = response.data; console.log(response) })
    },
    ordenarAnyo: function () {
      this.results.Search.sort((a, b) => b.Year - a.Year)
    }
  },
  name: 'buscadorPeliculas',
  components: {
    fichaPelicula,
    detallePelicula
  },
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
