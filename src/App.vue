<template>
  <div id="app">
    <Header-bool @ricercaFilm="funzioneRicercaFilm" />
    <Main-bool :array-films="arrayFilms" />
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
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";
</style>
