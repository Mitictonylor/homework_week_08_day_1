<template lang="html">
  <div class="">
<ul>
<list-item v-for="(film, index) in films" :key="index" :film="film"></list-item>
</ul>
</div>
</template>

<script>
import FilmListItem from './FilmListItem.vue'
export default {
  name:"FilmList",
  props:['films'],
  components: {
    'list-item': FilmListItem
  }
}
</script>

<style lang="css" scoped>
</style>
