<template lang="html">
  <div>
    <img src="@/assets/logo.svg" alt="">
    <film-list :films="films"></film-list>
    <film-detail v-if="selectedFilm" :selectedFilm="selectedFilm"></film-detail>
  </div>

</template>

<script>
import FilmList from '@/components/FilmList.vue'
import{eventBus} from '../main.js'
import FilmDetail from '@/components/FilmDetail.vue'
export default {
  name:"home",
  data(){
    return{
          films:null,
          selectedFilm: null
  }},
  components: {
    "film-list": FilmList,
    'film-detail':FilmDetail

  },
  mounted(){
    fetch('https://swapi.dev/api/films/').then(res => res.json())
    .then(data => this.films = data.results)

    eventBus.$on('film-selected', (film) =>{
      this.selectedFilm = film})
  }
}
</script>

<style lang="css" scoped>
</style>
