<template>
    <div class="comic-card">
        <h2 class="comic-titulo">
            {{ comic.titulo }}
        </h2>
        <button @click="seleccionarFavorito()" class="btn-favorito">
            Seleccionar favorito
        </button>
        <button @click="deleteComic()" class="btn-favorito">
            Eliminar Comic
        </button>
        <p class="comic-descripcion">
            {{ comic.descripcion }} <br/>
            {{ index }}
        </p>
        <div class="imagen-container">
            <img id="comic" :src="comic.imagen" :alt="comic.titulo"/>
        </div>
        <h4 class="comic-year" :class="{
        rojo: comic.year <= 2000,
        verde: comic.year > 2000
        }">
            Año: {{ comic.year }}
        </h4>
    </div>
</template>

<script>
export default {
    name: 'ComicComponent',
    props: ["comic", "index"],
    methods: {
        seleccionarFavorito() {
            console.log(this.comic);
            this.$emit("seleccionarFavorito", this.comic);
        }, deleteComic() {
            this.$emit("deleteComic", this.index);
        }
    }
}
</script>

<style>
    @import '../assets/css/comics.css';
</style>