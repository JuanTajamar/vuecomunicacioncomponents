<template>
  <div class="comics-container">
    <h2 class="titulo-principal">Padre comics</h2>
    
    <!-- Formulario para crear nuevo comic -->
    <div class="form-section">
      <h3 class="form-title">Crear Nuevo Comic</h3>
      <form @submit.prevent="crearComic" class="comic-form">
        <input v-model="nuevoComic.titulo" type="text" placeholder="Título" required class="form-input" />
        <input v-model="nuevoComic.descripcion" type="text" placeholder="Descripción" required class="form-input" />
        <input v-model="nuevoComic.imagen" type="url" placeholder="URL de la imagen" required class="form-input" />
        <input v-model.number="nuevoComic.year" type="number" placeholder="Año" required class="form-input" />
        <button type="submit" class="btn-crear">Crear Comic</button>
      </form>
    </div>

    <div class="favorito-section">
      <h3 class="favorito-label">Comic Favorito:</h3>
      <div v-if="comicFavorito" class="favorito-card-container">
        <div class="comic-card comic-card-favorito">
            <div class="favorito-badge">FAVORITO</div>
            <h2 class="comic-titulo">
                {{ comicFavorito.titulo }}
            </h2>
            <p class="comic-descripcion">
                {{ comicFavorito.descripcion }}
            </p>
            <div class="imagen-container">
                <img id="comic" :src="comicFavorito.imagen" :alt="comicFavorito.titulo"/>
            </div>
            <h4 class="comic-year" :class="{
            rojo: comicFavorito.year <= 2000,
            verde: comicFavorito.year > 2000
            }">
                Año: {{ comicFavorito.year }}
            </h4>
        </div>
      </div>
      <span v-else class="favorito-placeholder">Selecciona tu favorito</span>
    </div>
    <div id="comics" v-for="(comic, index) in comics" :key="index">
        <ComicComponent :comic="comic" :index="index" 
        v-on:seleccionarFavorito="seleccionarFavorito"
        v-on:deleteComic="deleteComic"/>
    </div>
  </div>
</template>

<script>
import ComicComponent from "./ComicComponent.vue";
export default {
  name: "ComicsComponent",
  components: {
    ComicComponent,
  }, methods: {
    seleccionarFavorito(comic) {
        console.log(comic.titulo);
        this.comicFavorito = comic;
    },
    crearComic() {
      // Crear una copia del nuevo comic y añadirlo al array
      this.comics.push({ ...this.nuevoComic });
      
      // Limpiar el formulario
      this.nuevoComic = {
        titulo: '',
        descripcion: '',
        imagen: '',
        year: null
      };
    },
    deleteComic(index) {
        this.comics.splice(index, 1);
    }
  },
  data() {
    return {
      comicFavorito: null,
      nuevoComic: {
        titulo: '',
        descripcion: '',
        imagen: '',
        year: null
      },
      comics: [
        {
          titulo: "Spiderman",
          imagen:
            "https://3.bp.blogspot.com/-i70Zu_LAHwI/T290xxduu-I/AAAAAAAALq8/8bXDrdvW50o/s1600/spiderman1.jpg",
          descripcion: "Hombre araña",
          year: 1997,
        },
        {
          titulo: "Wolverine",
          imagen:
            "https://images-na.ssl-images-amazon.com/images/I/51c1Q1IdUBL._SX259_BO1,204,203,200_.jpg",
          descripcion: "Lobezno",
          year: 2003,
        },
        {
          titulo: "Guardianes de la Galaxia",
          imagen:
            "https://tienda.tomosygrapas.com/61160-large_default/guardianes-de-la-galaxia-99-06.jpg",
          descripcion: "Yo soy Groot",
          year: 2006,
        },
        {
          titulo: "Avengers",
          imagen:
            "https://d26lpennugtm8s.cloudfront.net/stores/057/977/products/ma_avengers_01_01-891178138c020318f315132687055371-640-0.jpg",
          descripcion: "Los Vengadores",
          year: 1993,
        },
        {
          titulo: "Spawn",
          imagen:
            "https://i.pinimg.com/originals/e1/d8/ff/e1d8ff4aeab5e567798635008fe98ee1.png",
          descripcion: "Al Simmons",
          year: 2000,
        },
        {
          titulo: "Batman",
          imagen:
            "https://www.comicverso.com/wp-content/uploads/2020/06/The-Killing-Joke-657x1024.jpg",
          descripcion: "Murcielago",
          year: 2001,
        },
      ],
    };
  },
};
</script>

<style scoped>
.comics-container {
  max-width: 1400px;
  margin: 2rem auto;
  padding: 2rem;
  background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
  border-radius: 20px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
}

.titulo-principal {
  color: white;
  text-align: center;
  font-size: 3rem;
  margin-bottom: 2rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 800;
  letter-spacing: 1px;
}

/* Estilos del formulario */
.form-section {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  padding: 1.5rem;
  border-radius: 15px;
  margin-bottom: 2rem;
  border: 2px solid rgba(255, 255, 255, 0.2);
}

.form-title {
  color: #4facfe;
  text-align: center;
  font-size: 1.5rem;
  margin: 0 0 1rem 0;
  font-weight: 700;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
}

.comic-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 600px;
  margin: 0 auto;
}

.form-input {
  padding: 12px 16px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.9);
  font-size: 1rem;
  transition: all 0.3s ease;
  outline: none;
}

.form-input:focus {
  border-color: #4facfe;
  box-shadow: 0 0 10px rgba(79, 172, 254, 0.5);
  background: white;
}

.form-input::placeholder {
  color: #999;
}

.btn-crear {
  padding: 14px 20px;
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  color: white;
  border: none;
  border-radius: 12px;
  font-size: 1.1rem;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(79, 172, 254, 0.4);
}

.btn-crear:hover {
  background: linear-gradient(135deg, #00f2fe 0%, #4facfe 100%);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(79, 172, 254, 0.6);
}

.btn-crear:active {
  transform: translateY(0);
}

.favorito-section {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  padding: 1.5rem;
  border-radius: 15px;
  margin-bottom: 2rem;
  text-align: center;
  border: 2px solid rgba(255, 255, 255, 0.2);
}

.favorito-label {
  color: #ffd700;
  font-size: 1.5rem;
  margin: 0 0 0.5rem 0;
  font-weight: 700;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
}

.favorito-card-container {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.comic-card-favorito {
  position: relative;
  border: 4px solid #ffd700 !important;
  box-shadow: 0 0 30px rgba(255, 215, 0, 0.5), 0 8px 30px rgba(0, 0, 0, 0.15) !important;
  animation: pulse 2s infinite;
}

.favorito-badge {
  position: absolute;
  top: -15px;
  left: 50%;
  transform: translateX(-50%);
  background: linear-gradient(135deg, #ffd700 0%, #ffed4e 100%);
  color: #1e3c72;
  padding: 0.5rem 1.5rem;
  border-radius: 20px;
  font-weight: 900;
  font-size: 0.9rem;
  box-shadow: 0 4px 15px rgba(255, 215, 0, 0.6);
  letter-spacing: 1px;
  z-index: 10;
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 0 30px rgba(255, 215, 0, 0.5), 0 8px 30px rgba(0, 0, 0, 0.15);
  }
  50% {
    box-shadow: 0 0 50px rgba(255, 215, 0, 0.8), 0 8px 30px rgba(0, 0, 0, 0.15);
  }
}

.favorito-placeholder {
  color: rgba(255, 255, 255, 0.6);
  font-size: 1.2rem;
  font-style: italic;
}

#comics {
  display: inline-block;
  margin: 1rem;
  animation: fadeInUp 0.5s ease-out;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .comics-container {
    padding: 1rem;
  }
  
  .titulo-principal {
    font-size: 2rem;
  }
  
  .favorito-card-container {
    padding: 0;
  }
}
</style>