<template lang="html">
<div>
  <router-link :to="{name: 'crawl', params: {selectedFilm}}">Title: {{selectedFilm.title}}</router-link>
  <p>Episode: {{selectedFilm.episode_id}}</p>
  <p>Release Date: {{selectedFilm.release_date |moment("Do MMM YYYY")}}</p>
  <p>Director: {{selectedFilm.director}}</p>
  <p>Characters: </p>
<ul>
<character-detail v-for="(character,index) in characters" :key="index" :character="character"></character-detail>
</ul>
</div>
</template>

<script>
import CharacterDetail from './CharacterDetail'
export default {
  name:'FilmDetail',
  props:["selectedFilm"],
  data(){
    return{
      characters:[]

    }
  },
  methods:{
    getCharacters: function(){
      //fetch all episodes
      const charactersPromises = this.selectedFilm.characters.map((characterUrl) => {
        return fetch(characterUrl).then(res => res.json())//will give us an array of promises
      })
      Promise.all(charactersPromises)
      .then(data => this.characters = data);//takes in the array of promises, return as another promise and will execute the json, and bring us back the data
    },


  },
  components:{
    'character-detail': CharacterDetail
  },
  mounted(){
    //as soon as this page is charged will invoke the function
    this.getCharacters()

  },
  watch:{
    selectedFilm: function(){
      this.getCharacters()
    }
  },

}
</script>

<style lang="css" scoped>
</style>
