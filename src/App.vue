<template>
  <PadreDeportes/>
  <HijoDeportes/>
</template>

<script>
import PadreDeportes from './components/PadreDeportes.vue'
import HijoDeportes from './components/HijoDeportes.vue'

export default {
  name: 'App',
  components: {
    PadreDeportes,
    HijoDeportes
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
