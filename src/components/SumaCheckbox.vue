<template>
  <div>
    <h1>Generador Checkbox</h1>
    <button @click="generarRandom">Generar CheckBox</button>
    <div v-for="numero in numeros"  :key="numero">
        <label for="input">{{ numero }}</label>
        <input type="checkbox" @click="sumarNumeros" :value="numero"/>
    </div>
    <h2>La suma es: {{ suma }}</h2>
  </div>
</template>

<script>
export default {
    name:"GenerarCheckbox",
    data(){
        return{
            numeros:[],
            suma: 0,
        }
    },
    methods:{
        generarRandom(){
            this.numeros = [];
            for (let i = 0; i < parseInt(Math.random() * 10) + 1; i++) {
                this.numeros.push(parseInt(Math.random() * 100) + 1)
            }
        },
        sumarNumeros($event){
            if ($event.target.checked) {
                this.suma += parseInt($event.target.value)
            }else{
                this.suma -= parseInt($event.target.value)
            }
        }
    }
}
</script>
<style scoped>
div {
  max-width: 640px;
  margin: 20px auto;
  padding: 14px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  font-family: Arial, Helvetica, sans-serif;
  color: #222;
}

h1 {
  font-size: 1.25rem;
  margin: 0;
}

button {
  background: #2b8aef;
  color: #fff;
  border: none;
  padding: 8px 14px;
  border-radius: 8px;
  cursor: pointer;
  transition: transform 0.12s ease, box-shadow 0.12s ease;
}

button:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 12px rgba(43,138,239,0.18);
}

div > div {
  display: flex;
  gap: 10px;
  align-items: center;
  flex-wrap: wrap;
  justify-content: center;
  width: 100%;
  padding: 6px 0;
}

input[type="checkbox"] {
  width: 18px;
  height: 18px;
  cursor: pointer;
}

label {
  font-size: 1rem;
  margin-right: 8px;
  user-select: none;
}

h2 {
  margin: 8px 0 0;
  background: #f7fafc;
  padding: 8px 12px;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.04);
}
</style>