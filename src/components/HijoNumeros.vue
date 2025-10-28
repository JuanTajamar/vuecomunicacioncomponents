<template>
  <div>

    <h4>Número hijo {{ numero }}</h4>
    <button @click="sumarNumero">Sumar {{ numero }}</button>
  </div>
</template>

<script>
    export default {
        name: "HijoNumeros",
        props: ["numero"],
        methods: {
            sumarNumero() {
                this.$emit("sumarNumero", this.numero)
            }
        }
    }
</script>

<style>

</style>