<template>
    <div>
        Aqui ira el detalle de la pelicula
        {{idPelicula}}
    </div>
</template>
<script>

export default {
  data () {
    return {

    }
  },
  props: {
    idPelicula: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
