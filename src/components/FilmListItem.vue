<template lang="html">
  <div class="light-background">
<li v-on:click="handleClick">{{film.title}}</li>
</div>
</template>

<script>
import{eventBus} from '../main.js'
export default {
  name:"FilmListItem",
  props:['film'],
  methods: {
    handleClick: function(){
      eventBus.$emit('film-selected', this.film)
    }
  }
}
</script>

<style lang="css" scoped>

</style>
