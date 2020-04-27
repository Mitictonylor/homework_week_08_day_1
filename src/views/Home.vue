<template lang="html">
  <div>
    <img src="@/assets/logo.svg" alt="">
    <film-list class='light-background' :films="films"></film-list>
    <film-detail  class='light-background' v-if="selectedFilm" :selectedFilm="selectedFilm"></film-detail>
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

<style lang="css">
.light-background{
  background-color: rgba(255,255,255, 0.35);
  padding: 5px;
  margin: 0px auto 0px auto;
  display: inline;
  width: 100%;
  display: table;

}

</style>
