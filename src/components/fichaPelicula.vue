<template>
      <b-card
        :img-src=movie.Poster
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;">
        <b-card-text>
              <h3 class="card-text">{{movie.Title}}</h3>
              <h4 class="card-text">{{movie.Year}}</h4>
              <b-button :href="'https://www.imdb.com/title/'+movie.imdbID+'/'" target="_blank" variant="primary">Ir a imdb</b-button>
              <b-button @click="verInfo" href="#"  variant="primary">Ver más</b-button>
        </b-card-text>
      </b-card>
</template>
<script>

export default {
  data () {
    return {

    }
  },
  props: {
    movie: Object
  },
  methods: {
    verInfo: function () {
      this.$emit('verDetalle', this.movie.imdbID)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
