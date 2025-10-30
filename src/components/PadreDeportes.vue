<template>
    <div>
        <h1 style="color:blue">Padre deportes</h1>
        <h2 style="background-color: yellow;" v-if="favorito">Su deporte favorito es {{ favorito }}</h2>
        <ul>
            <li v-for="sport in deportes" :key="sport">
                <HijoDeportes :nombredeporte="sport"
                v-on:seleccionarFavoritoParent="seleccionarFavoritoParent"/>

            </li>
        </ul>
    </div>
</template>

<script>
import HijoDeportes from './HijoDeportes.vue';
    export default {
        name: "PadreDeportes",
        components: {
            HijoDeportes
        },
        data() {
            return {
                deportes: ["Curling", "Peonza", "Canicas", "Bolos"],
                favorito: null
            }
        },methods: {
            seleccionarFavoritoParent(deporteFavorito) {
                console.log("Yo soy tu padre")
                this.favorito = deporteFavorito
            }
        }
    }
</script>

<style>
    button {
        background-color: #0d6efd;
        color: #fff;
        border: none;
        padding: 8px 16px;
        border-radius: 4px;
        cursor: pointer;
        transition: background-color 0.2s ease, transform 0.1s ease;
    }

    button:hover {
        background-color: #0b5ed7;
        transform: translateY(-1px);
    }

    button:active {
        transform: translateY(0);
    }

    button:focus {
        outline: 3px solid rgba(13, 110, 253, 0.25);
        outline-offset: 2px;
    }
</style>