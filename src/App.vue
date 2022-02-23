<template>
  <div id="app">
    <ContainerAlbum></ContainerAlbum>
  </div>
</template>

<script>
import ContainerAlbum from './components/ContainerAlbum.vue'

export default {
  name: 'App',

  components: {
    ContainerAlbum
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss"
</style>
