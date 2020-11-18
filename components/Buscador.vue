<template>
  <div class="buscador">
    <b-form inline>
      <b-form-input
        id="inline-form-input-name"
        class="mb-2 mr-sm-2 mb-sm-0"
        v-model="nombrePersonaje"
        placeholder="Buscar Personaje"
        @keydown.enter.prevent="selectC"
      ></b-form-input>
      <b-button
        :disabled="nombrePersonaje == ''"
        @click="selectC"
        variant="info"
        >Buscar</b-button
      >
    </b-form>
  </div>
</template>
<script>
export default {
  name: "Buscador",
  data() {
    return {
      nombrePersonaje: ""
    };
  },
  methods: {
    selectC() {
      this.$emit("select", this.nombrePersonaje);
    }
  }
  /*   updated() {
    this.$emit("nombrePersonaje", this.nombrePersonaje);
  } */
};
</script>
<style lang="scss"></style>
