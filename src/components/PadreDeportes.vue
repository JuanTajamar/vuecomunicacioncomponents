<template>
  <div>
    <h1>Soy padre</h1>
    <ul>
        <li v-for="sport in deportes" :key="sport">
            <HijoDeportes :nombredeporte="sport"/>
        </li>
        
    </ul>
  </div>
</template>

<script>
import HijoDeportes from './HijoDeportes'
export default {
    name: "PadreDeportes",
    components: {
        HijoDeportes
    },
    data() {
        return {
            deportes: ["Futbol", "Poker", "Blackjack", "Petanca"]
        }
    }
}
</script>

<style>

</style>
