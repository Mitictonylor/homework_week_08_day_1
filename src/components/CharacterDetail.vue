<template lang="html">
<div >
  <li>Name: {{character.name}}</li>
  <li>Height: {{character.height |fixHeight}} </li>
  <li>Homeworld name: {{homeworld.name}}</li>
  <li>Homeworld terrain: {{homeworld.terrain}}</li>
  <hr>
</div>
</template>

<script>
export default {
  name:'CharacterDetail',
  props:['character'],
  data(){
    return{
      homeworld: []
    }
  },
  methods:{
    getHomeworld: function(){
      fetch(this.character.homeworld).then(res => res.json()).then(data => this.homeworld = data)
    }
  },
  mounted(){
    this.getHomeworld()
  },
  filters:{
    fixHeight: function(height){
      const toM = (height * 0.01).toFixed(2)
      return toM + " m"
    }

    }
  }



</script>

<style lang="css" scoped>
</style>
