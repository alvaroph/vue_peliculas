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
        </b-card-text>
        <b-button href="#" variant="primary">Go somewhere</b-button>
        </b-card>
        {{datosPelicula}}
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
