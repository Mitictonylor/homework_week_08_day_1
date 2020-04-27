<template lang="html">
  <div class="light-background">

    <router-view id="view"></router-view>
  </div>

</template>

<script>

export default {
  name:"app"

}
</script>

<style lang="css" scoped>
.light-background{
  background-color: rgba(255,255,255, 0.35);
  padding: 5px;
  margin: 0;
  display: block;
  width: 100%;
}

</style>
