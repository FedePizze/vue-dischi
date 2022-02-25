<template>
  <div id="app">
    <HeaderAlbum :generi="arreyGeneri" @genereScelto='getRisposta'></HeaderAlbum>
    <ContainerAlbum @generi='getGeneri' :soluzione="portingGenere"></ContainerAlbum>
  </div>
</template>

<script>
import ContainerAlbum from './components/ContainerAlbum.vue'
import HeaderAlbum from './components/HeaderAlbum.vue'

export default {
  name: 'App',

  components: {
    HeaderAlbum,
    ContainerAlbum
  },

  data() {
    return {
      arreyGeneri: [],
      portingGenere: '',
    }
  },

  methods: {
    getGeneri(genreAlbum) {

      this.arreyGeneri = genreAlbum
    },

   getRisposta(genere) {

    this.portingGenere = genere
    console.log(this.portingGenere)
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss"
</style>
