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
    };
  },
  methods: {
    ricercaFilm() {
      if (this.FilmCercato == "") {
        this.arrayFilms = "";
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=${this.FilmCercato}`
          )
          .then((response) => {
            console.log(response);
            this.arrayFilms = response.data.results;
            console.log(this.arrayFilms);
            this.$emit("ricercaFilm", this.arrayFilms);
          });
        this.FilmCercato = "";
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
