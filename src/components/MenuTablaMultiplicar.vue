<template>
  <div>
    <ul id="menu">
        <li><router-link to="/">Padre</router-link></li>
        <li v-for="num in numeros" :key="num"><router-link :to="'/tablamultiplicar/' + num">Tabla multiplicar {{ num }}</router-link></li> 
    </ul>
  </div>
</template>

<script>
    export default {
        name: "MenuComponent",
        data(){
            return {
                numeros: 0
            }
        }, mounted() {
                this.numeros = []
                for (let i = 0; i < 4; i++) {
                    let random = parseInt((Math.random() * 50) + 1)
                    this.numeros.push(random)
                }
        }
    }
</script>

<style scoped>
/* Contenedor del menú */
div {
  max-width: 900px;
  margin: 18px auto;
  padding: 12px 18px;
  background: linear-gradient(180deg, #ffffff 0%, #fbfdff 100%);
  border-radius: 10px;
  box-shadow: 0 6px 18px rgba(28, 45, 60, 0.08);
  font-family: Inter, "Segoe UI", Roboto, "Helvetica Neue", Arial;
}

/* Título */
h1 {
  margin: 0 0 10px 0;
  font-size: 1.15rem;
  color: #1c2d3c;
  font-weight: 600;
}

/* Lista horizontal, centrada y con separación consistente */
ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  gap: 12px;
  align-items: center;
  flex-wrap: wrap;
}

/* Cada elemento como bloque para que el enlace reciba padding */
li {
  display: block;
}

/* Enlaces estilo "pill" limpio y accesible */
li a {
  display: inline-block;
  padding: 8px 14px;
  color: #1c6b4a; /* color principal */
  background: transparent;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.95rem;
  text-decoration: none;
  transition: all 180ms ease;
  border: 1px solid transparent;
  box-shadow: none;
}

/* Hover: sutil elevación y fondo suave */
li a:hover,
li a:focus {
  color: #ffffff;
  background: linear-gradient(90deg, #2aa876, #1f9c6f);
  transform: translateY(-2px);
  box-shadow: 0 6px 14px rgba(37, 136, 93, 0.14);
  outline: none;
  border-color: rgba(0,0,0,0.03);
}

/* Estado activo provisto por Vue Router (.router-link-active) */
.router-link-active {
  color: #ffffff !important;
  background: linear-gradient(90deg, #1f9c6f, #13805a);
  box-shadow: 0 8px 20px rgba(19, 128, 90, 0.15);
  transform: translateY(-2px);
}

/* Focus visible para accesibilidad */
li a:focus-visible {
  outline: 3px solid rgba(33, 150, 83, 0.18);
  outline-offset: 2px;
}

/* Responsive: en pantallas pequeñas apilar verticalmente */
@media (max-width: 520px) {
  ul {
    flex-direction: column;
    gap: 8px;
  }
  li a {
    width: 100%;
    text-align: center;
    padding: 10px 12px;
  }
}
</style>