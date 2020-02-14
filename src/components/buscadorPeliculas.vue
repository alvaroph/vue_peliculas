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
          <fichaPelicula :datos=query></fichaPelicula>
          <b-row>
            <b-col cols="4"  v-for="actual in results.Search" :key="actual.imdbID">
              <fichaPelicula  :movie=actual></fichaPelicula>
            </b-col>
          </b-row>
        </b-col>
        <b-col cols="1"></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

import fichaPelicula from '@/components/fichaPelicula.vue'
import axios from 'axios'

export default {
  data () {
    return {
      query: '',
      results: []
    }
  },
  methods: {
    hazQuery: function () {
      axios.get(`http://www.omdbapi.com/?apikey=19f8a30e&s=${this.query}`).then(response => { this.results = response.data; console.log(response) })
    },
    ordenarAnyo: function () {
      this.results.Search.sort((a, b) => b.Year - a.Year)
    }
  },
  name: 'buscadorPeliculas',
  components: {
    fichaPelicula
  },
  props: {
    datos: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
