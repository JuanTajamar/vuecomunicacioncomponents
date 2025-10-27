<template>
  <div>
    <h2>{{ nombredeporte }}</h2>
  </div>
</template>

<script>
    export default {
        name: "HijoDeportes",
        props: ["nombredeporte"],
        mounted() {
            console.log(this.nombredeporte)
        }
    }
</script>

<style>

</style>