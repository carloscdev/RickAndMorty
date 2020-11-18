<template>
  <b-navbar toggleable="lg" type="dark" class="navbar">
    <b-navbar-brand>
      <nuxt-link to="/">
      <img src="../assets/images/logo.png" alt="Logo Rick Morty" />
      </nuxt-link>
    </b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-item-dropdown text="Otros Proyectos" right>
          <b-dropdown-item href="https://reproductormusica.netlify.app/" target="_blank" ref="noreferrer noopener">Spotify Api</b-dropdown-item>
          <b-dropdown-item href="https://carloscdev.github.io/PiedraPapelTijera/" target="_blank" ref="noreferrer noopener">Piedra,Papel,Tijera</b-dropdown-item>
          <b-dropdown-item href="https://simondice-lu3cey0iq.vercel.app/" target="_blank" ref="noreferrer noopener">Simon Dice</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>
<script>
export default {
  name: "Navbar"
};
</script>
<style lang="scss">
.navbar {
  background-color: rgba($color: #000000, $alpha: 0.8);
  position: fixed;
  width: 100%;
  z-index: 9;
  img {
    width: 150px;
  }
}
</style>
