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
          <div>{{ personaje.status }} - {{ personaje.species }}</div>
        </div>
      </b-card-body>
      <b-card-footer class="fondo">
        <nuxt-link class="btn-detail" :to="'/personajes/' + personaje.id">
          Ver Detalles
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
<style lang="scss">
.fondo {
  background-color: var(--color-celeste);
  transition: all 400ms ease;
  &:hover {
    background-color: var(--color-celeste2);
  }
}
.btn-detail {
  display: block;
  padding: 1vw;
  color: var(--color-blanco);
  text-align: center;

  &:hover {
    color: var(--color-blanco);
    text-decoration: none;
  }
}
.personaje__info {
  display: flex;
  align-items: center;
}
.personaje__card {
  border-radius: 20px;
  overflow: hidden;
}
.rojo {
  background-color: var(--color-rojo);
}
.plomo {
  background-color: var(--color-morado);
}
.status {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  margin-right: 1em;
}
.verde {
  background-color: var(--color-verde);
}
</style>
