<template>
  <div>
    <b-card
      no-body
      :img-src="personaje.image"
      :img-alt="personaje.name"
      img-top
      tag="article"
      class="personaje__card"
    >
      <b-card-body>
        <h3 class="mb-0">{{ personaje.name }}</h3>
        <br>
        <div class="personaje__info">         
          <div
            class="status"
            :class="
              personaje.status === 'Alive'
                ? 'verde'
                : personaje.status === 'Dead'
                ? 'rojo'
                : 'plomo'
            "
          ></div>        
          <div>{{ personaje.status }}</div>     
        </div> 
         <div> Especie: {{ (personaje.species) == '' ? 'No definido' :personaje.species }} <br>
          Tipo: {{(personaje.type) == '' ? 'No definido' : personaje.type}} <br>
          Genero: {{(personaje.gender) == '' ? 'No definido' :personaje.gender}} <br>
          Origen: {{(personaje.origin.name) == '' ? 'No definido' :personaje.origin.name}} <br>
          Locación: {{(personaje.location.name) == '' ? 'No definido' :personaje.location.name}} 
          </div>
      </b-card-body>
      <b-card-footer class="fondo">
        <nuxt-link class="btn-detail" to="/">
          Volver a inicio
        </nuxt-link></b-card-footer
      >
    </b-card>
  </div>
</template>
<script>
export default {
  name: "Personajes",
  props: {
    personaje: { type: Object, required: true }
  }
};
</script>

