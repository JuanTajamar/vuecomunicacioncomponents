<template>
  <div>
    <h1>NÚMEROS PADRE</h1>
    <h2>La suma es: {{ suma }}</h2>
    <button @click="generarNuevoNumero">Nuevo numero</button>
    <h2 v-for="numero in numeros" :key="numero"><HijoNumeros :numero="numero" v-on:sumarNumero="sumarNumero"/></h2>
  </div>
</template>

<script>
import HijoNumeros from './HijoNumeros.vue'
    export default {
        name: "PadreNumeros",
        components: {
            HijoNumeros
        }, data() {
            return {
                numeros: [4,6,8],
                suma: null
            }
        }, methods: {
            generarNuevoNumero () {
                let newNumber = parseInt((Math.random() * 50) + 1)
                this.numeros.push(newNumber)
            },
            sumarNumero(numero) {
                this.suma += numero
            }
        }
    }
</script>

<style>

</style>