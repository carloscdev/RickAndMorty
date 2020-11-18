<template>
  <div class="hero">
    <div class="hero__contenedor">
      <div class="hero__contenedor--titulo"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Hero"
};
</script>
<style lang="scss">
.hero {
  min-height: 700px;
  background-image: url("../assets/images/banner.jpg");
  background-size: cover;
  background-position: center;
  @media (max-width: 768px) {
    min-height: 400px;
  }
}
</style>
