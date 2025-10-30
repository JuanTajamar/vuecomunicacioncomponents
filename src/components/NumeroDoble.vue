<template>
  <div>
    <h1>Numero doble: {{ doble }}</h1>
    <h2 style="color:red">{{ mensaje }}</h2>
    <button @click="redirectToHome()">Home</button>
  </div>
</template>

<script>
    export default {
        name: "NumeroDoble",
        methods:{
            redirectToHome(){
                this.$router.push("/")
            }
        },
        data(){
            return {
                mensaje: "",
                doble: 0
            }
        },
        mounted(){
            console.log("Param: " + this.$route.params.numero)
            // Los parametros siempre son string, no importa si son numericos
            let numero = this.$route.params.numero;
            if (numero == "") {
                this.mensaje = "Sin paramentros en Routing"
            } else {
                this.mensaje = "Parametro recibido: " + numero
                this.doble = parseInt(numero) * 2;
            }
        }, watch: {
            '$route.params.numero' (nextVal, oldVal) {
                if (nextVal != oldVal) {
                    this.mensaje = "Esto ha cambiado: " + this.$route.params.numero
                    this.doble = parseInt(this.$route.params.numero) 
                    console.log("Next: " + nextVal)
                    console.log("Old: " + oldVal)
                }                
            }
        }
    }
</script>

<style scoped>
    /* Contenedor principal centrado */
    div {
    max-width: 600px;
    margin: 0 auto;
    padding: 32px 24px;
    background: linear-gradient(180deg, #ffffff 0%, #fbfdff 100%);
    border-radius: 12px;
    box-shadow: 0 6px 18px rgba(28, 45, 60, 0.08);
    font-family: Inter, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    text-align: center;
    
    /* Centrado vertical */
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    }

    /* Títulos */
    h1 {
    margin: 0 0 16px 0;
    font-size: 2rem;
    color: #1c2d3c;
    font-weight: 700;
    letter-spacing: -0.5px;
    }

    h2 {
    margin: 0 0 24px 0;
    font-size: 1.1rem;
    font-weight: 500;
    padding: 12px 18px;
    background: linear-gradient(135deg, #fee2e2 0%, #fecaca 100%);
    border-left: 4px solid #ef4444;
    border-radius: 8px;
    color: #dc2626 !important;
    box-shadow: 0 2px 8px rgba(220, 38, 38, 0.1);
    }

    /* Botón mejorado */
    button {
    padding: 12px 24px;
    background: linear-gradient(90deg, #1f9c6f, #13805a);
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    font-weight: 600;
    transition: all 180ms ease;
    box-shadow: 0 4px 12px rgba(31, 156, 111, 0.2);
    margin-top: 8px;
    }

    button:hover {
    background: linear-gradient(90deg, #2aa876, #1f9c6f);
    transform: translateY(-2px);
    box-shadow: 0 6px 16px rgba(31, 156, 111, 0.3);
    }

    button:active {
    transform: translateY(0);
    box-shadow: 0 2px 8px rgba(31, 156, 111, 0.25);
    }

    button:focus-visible {
    outline: 3px solid rgba(31, 156, 111, 0.3);
    outline-offset: 2px;
    }

    /* Responsive */
    @media (max-width: 520px) {
    div {
        padding: 24px 18px;
        max-width: 90%;
    }
    
    h1 {
        font-size: 1.6rem;
    }
    
    h2 {
        font-size: 1rem;
    }
    }
</style>