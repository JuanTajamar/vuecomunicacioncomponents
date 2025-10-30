<template>
  <div class="table-container">
    <h2>Tabla de multiplicar del {{ $route.params.numero }}</h2>
    <table class="multiplication-table">
      <thead>
        <tr>
          <th>Operación</th>
          <th>Resultado</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="i in 10" :key="i">
          <td>{{ $route.params.numero }} x {{ i }}</td>
          <td>{{ $route.params.numero * i }}</td>
        </tr>
      </tbody>
    </table>
    <button @click="redirectToHome">Volver</button>
  </div>
</template>

<script>
export default {
    name: 'TablaMultiplicar',
    mounted() {
        console.log("Param: " + this.$route.params.numero);
        let numero = this.$route.params.numero;
        //AQUI HACEMOS LA LÓGICA DE LA TABLA DE MULTIPLICAR
        this.resultados = [];
        for (let i = 1; i <= 10; i++) {
            this.resultados.push(numero * i);
        }
    },
    data() {
        return {
            resultados: []
        }
    },
    methods: {
    redirectToHome() {
            this.$router.push('/')
        }
    }
}
</script>

<style scoped>
    div {
        max-width: 700px;
        margin: 20px auto;
        padding: 36px 28px;
        background: linear-gradient(180deg, #ffffff 0%, #f8fafc 100%);
        border-radius: 16px;
        box-shadow: 0 10px 30px rgba(28, 45, 60, 0.12);
        font-family: Inter, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }

    table {
        width: 100%;
        border-collapse: separate;
        border-spacing: 0;
        border-radius: 10px;
        overflow: hidden;
    }

    thead tr {
        background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
        color: white;
    }

    th {
        padding: 16px 20px;
        text-align: center;
        font-weight: 600;
        font-size: 1.1rem;
    }

    td {
        padding: 16px 20px;
        font-size: 1.1rem;
        font-weight: 500;
        color: #1e40af;
        background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
        border-bottom: 2px solid white;
        transition: all 200ms cubic-bezier(0.4, 0, 0.2, 1);
    }

    tr {
        animation: slideIn 0.4s ease-out backwards;
    }

    tr:hover td {
        background: linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%);
        transform: translateX(8px);
    }

    tr:nth-child(even) td {
        background: linear-gradient(135deg, #faf5ff 0%, #f3e8ff 100%);
        color: #7e22ce;
    }

    tr:nth-child(even):hover td {
        background: linear-gradient(135deg, #f3e8ff 0%, #e9d5ff 100%);
    }

    @keyframes slideIn {
        from {
            opacity: 0;
            transform: translateX(-20px);
        }
        to {
            opacity: 1;
            transform: translateX(0);
        }
    }

    /* Retraso escalonado para cada fila */
    tr:nth-child(1) { animation-delay: 0.05s; }
    tr:nth-child(2) { animation-delay: 0.1s; }
    tr:nth-child(3) { animation-delay: 0.15s; }
    tr:nth-child(4) { animation-delay: 0.2s; }
    tr:nth-child(5) { animation-delay: 0.25s; }
    tr:nth-child(6) { animation-delay: 0.3s; }
    tr:nth-child(7) { animation-delay: 0.35s; }
    tr:nth-child(8) { animation-delay: 0.4s; }
    tr:nth-child(9) { animation-delay: 0.45s; }
    tr:nth-child(10) { animation-delay: 0.5s; }

    @media (max-width: 640px) {
        div {
            padding: 24px 18px;
            max-width: 90%;
        }
        
        th, td {
            font-size: 1rem;
            padding: 14px 16px;
        }
    }
</style>