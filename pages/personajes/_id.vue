<template>
  <div class="detailPersonaje">
    <PersonajeDetail class="cardPersonaje" :personaje="personaje" />
  </div>
</template>
<script>
import axios from 'axios'
export default {
  asyncData({params}) {
    return axios.get(`https://rickandmortyapi.com/api/character/${params.id}`).then(res => {
      return {
        personaje: res.data
      
      }       
    })
  }
}
</script>
<style lang="scss">
  .detailPersonaje{
    min-height: 100vh;
    display: flex;
    align-items: center;
    width: 30%;
    margin: 0 auto;
    padding-top: 5vw;
    @media (max-width: 768px){
      width: 70%;
    }
    .cardPersonaje {
      width: 100%;
    }
  }
</style>