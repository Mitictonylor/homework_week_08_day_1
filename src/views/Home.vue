<template lang="html">
  <div class = "wrapper">
    <div class="logo">
    <img src="@/assets/logo.svg" width="300" height="150"alt="">
    </div>

    <div class = "film-list">
    <film-list :films="films"></film-list>
    </div>

    <div class = "film-details">
    <film-detail  class='light-background' v-if="selectedFilm" :selectedFilm="selectedFilm"></film-detail>
    </div>

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

.logo {
  display: inline;
   margin-left: 50%;
}
.wrapper {
  display: inline;


}
.film-list {
  width: 30%;
}

.film-details {
  width: 30%;
}
.light-background{
  color: yellow;
  font-size: 20px;
  padding: 5px;
  margin: 0px auto 0px auto;
  display: inline;
  width: 100%;
  display: table;

}

</style>
