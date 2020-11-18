<template>
  <div>
    <Hero />
    <div class="personajes__header contenedor">
      <h2>PERSONAJES</h2>
      <Buscador @select="Search" />
    </div>
    <div class="buscando" v-if="showSearch">
      <img class="girar" src="../assets/images/loader.png" alt="Loader" />
      <br />
      Buscando . . .
    </div>
    <div v-if="showLista" class="personajes__contenedor contenedor ">
      <div v-for="personaje in personajes" :key="personaje.id">
        <Personaje :personaje="personaje" />
      </div>
    </div>
    <div v-else>
      Sin resultados
    </div>
  </div>
</template>

<script>
import axios from "axios";
var pageNumber = 1;
export default {
  data() {
    return {
      personajes: [],
      pageNumber: 1,
      personajeNombre: "",
      showSearch: false,
      showLista : true
    };
  },
  asyncData() {
    return axios.get("https://rickandmortyapi.com/api/character/").then(res => {
      return {
        personajes: res.data.results,
        paginas: res.data.info
      };
    });
  },
  methods: {
    async Search(name) {
      this.showSearch = true;
      this.personajes = [];
      this.personajeNombre = name;
      return axios
        .get("https://rickandmortyapi.com/api/character/", {
          params: {
            name: this.personajeNombre
          }
        })
        .then(res => {
          setTimeout(() => {
            this.showSearch = false;
            this.personajes = res.data.results;
            this.showLista = true
          }, 1000);
        }).catch(() => { return(
          this.showSearch = false,
          this.showLista = false
        )});
    }
  }
};
</script>

<style lang="scss">
.personajes {
  &__contenedor {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-column-gap: 5em;
    grid-row-gap: 2em;
    @media (max-width: 1080px) {
      grid-template-columns: repeat(2, 1fr);
    }
    @media (max-width: 768px) {
      grid-template-columns: 1fr;
    }
  }
  &__header {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    align-items: center;
    .buscador {
      display: flex;
      justify-self: right;
    }
    @media (max-width: 768px) {
      grid-template-columns: 1fr;
      .buscador {
        justify-self: left;
        margin-bottom: 3em;
      }
    }
  }
}
@keyframes rotate360 {
  to {
    transform: rotate(360deg);
  }
}
.buscando {
  text-align: center;
  margin-top: 3em;
  margin-bottom: 3em;
  
  .girar {
    width: 20%;
    animation: 2s rotate360 infinite linear;
  }
}
</style>
