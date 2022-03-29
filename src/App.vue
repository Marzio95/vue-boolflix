<template>
  <div id="app">
    <Header-bool
      @ricercaFilm="funzioneRicercaFilm"
      @ricercaSerie="funzioneRicercaSerie"
    />
    <Main-bool :array-films="arrayFilms" :array-series="arraySeries" />
  </div>
</template>

<script>
import HeaderBool from "./components/HeaderBool.vue";
import MainBool from "./components/MainBool.vue";

export default {
  name: "App",
  data() {
    return {
      arrayFilms: null,
      arraySeries: null,
    };
  },
  components: {
    HeaderBool,
    MainBool,
  },
  methods: {
    funzioneRicercaFilm(arrayFilms) {
      this.arrayFilms = arrayFilms;
    },
    funzioneRicercaSerie(arraySeries) {
      this.arraySeries = arraySeries;
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";
</style>
