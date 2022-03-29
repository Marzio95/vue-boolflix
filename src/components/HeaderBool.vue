<template>
  <header class="header p-4">
    <h1>Boolflix</h1>
    <div>
      <input
        @keyup.enter="ricercaFilm()"
        type="text"
        name="film"
        id="film"
        placeholder="Cerca film"
        v-model="FilmCercato"
      />
      <button @click="ricercaFilm()">Cerca</button>
    </div>
  </header>
</template>

<script>
import axios from "axios";
export default {
  name: "HeaderBool",
  data() {
    return {
      FilmCercato: "",
      arrayFilms: null,
      arraySeries: null,
    };
  },
  methods: {
    ricercaFilm() {
      if (this.FilmCercato.trim() == "") {
        this.arrayFilms = null;
        this.$emit("ricercaFilm", this.arrayFilms);
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=9631e84004e35c8371fcb3c009af9551&query=${this.FilmCercato}`
          )
          .then((response) => {
            this.arrayFilms = response.data.results;
            this.$emit("ricercaFilm", this.arrayFilms);
          })
          .then(() => {
            axios
              .get(
                `https://api.themoviedb.org/3/search/tv?api_key=9631e84004e35c8371fcb3c009af9551&language=it_IT&query=${this.FilmCercato}`
              )
              .then((responseTV) => {
                this.arraySeries = responseTV.data.results;
                console.log(responseTV);
                this.$emit("ricercaSerie", this.arraySeries);
              });
          });
      }
    },
  },
};
</script>

<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: black;
}
h1 {
  color: red;
  text-transform: uppercase;
}
button {
  background-color: red;
  border: 1px solid black;
  color: white;
  height: 2.5rem;
  width: 5rem;
}
input {
  height: 2.5rem;
  width: 20rem;
}
</style>
