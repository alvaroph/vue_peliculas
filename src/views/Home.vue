<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <buscadorPeliculas datos="Esto es algo pasado a mi componente"></buscadorPeliculas>
  </div>
</template>

<script>
// @ is an alias to /src
import buscadorPeliculas from '@/components/buscadorPeliculas.vue'

export default {
  name: 'Home',
  components: {
    buscadorPeliculas
  }
}
</script>
