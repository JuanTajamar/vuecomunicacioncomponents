<template>
  <div>
    <form v-on:submit.prevent="mostrarSeleccionados">
      <select v-model="seleccionados" multiple size="8">
        <option>Elemento 1</option>
        <option>Elemento 2</option>
        <option>Elemento 3</option>
        <option>Elemento 4</option>
        <option>Elemento 5</option>
        <option>Elemento 6</option>
        <option>Elemento 7</option>
    </select>
    <button>Mostrar Seleccionados</button>
    </form>
    <h1>Seleccion sin boton (binding)</h1>
    <p>{{ this.seleccionados.join(", ") }}</p>
    <h1>Seleccion con boton</h1>
    <p>{{ mensaje }}</p>
  </div>
</template>

<script>
export default {
  name:"SeleccionMultiple",
  data(){
    return{
      seleccionados:[],
      mensaje:""
    }
  },
  methods:{
    mostrarSeleccionados(){
      this.mensaje = this.seleccionados.join(", ")
    }
  }
}
</script>


