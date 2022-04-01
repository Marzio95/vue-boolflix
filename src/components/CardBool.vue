<template>
  <div class="card p-2 col-2 text-center text-white bg-black">
    <img
      v-if="filmData.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342/' + filmData.poster_path"
      :alt="filmData.title"
    />
    <h5>{{ filmData.title }}</h5>
    <small
      v-show="
        filmData.title.toLowerCase() != filmData.original_title.toLowerCase()
      "
    >
      {{ filmData.original_title }}
    </small>
    <lang-flag
      class="flag"
      :iso="filmData.original_language"
      :squared="false"
    />
    <h6>{{ filmData.vote_average }}</h6>
    <div>
      <div class="star" v-for="element in fullArrayStars()" :key="element">
        &starf;
      </div>
      <small
        class="actor d-block"
        v-for="element in arrayAttori"
        :key="element.charater"
      >
        {{ element.name }}
      </small>
      <button
        @click="changeVisibilita"
        class="mt-4 d-block m-auto trama_button"
      >
        TRAMA
      </button>
      <small :class="visibilita == true ? 'd-block' : 'd-none'" class="trama"
        ><button @click="changeVisibilita" class="x">x</button
        >{{ filmData.overview }}</small
      >
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
import axios from "axios";

export default {
  name: "CardBool",
  data() {
    return {
      starf: "star",
      arrayStars: [],
      stars: Math.round(this.filmData.vote_average / 2),
      arrayAttori: [],
      visibilita: false,
    };
  },
  components: {
    LangFlag,
  },
  props: {
    filmData: Object,
  },
  methods: {
    fullArrayStars() {
      return this.stars;
    },
    changeVisibilita() {
      if (this.visibilita == false) {
        this.visibilita = true;
      } else {
        this.visibilita = false;
      }
    },
  },
  created() {
    axios
      .get(
        `https://api.themoviedb.org/3/movie/${this.filmData.id}/credits?api_key=9631e84004e35c8371fcb3c009af9551`
      )
      .then((response) => {
        this.arrayAttori = response.data.cast;
      })
      .then(() => {
        this.arrayAttori.splice(5, this.arrayAttori.length);
      });
    return this.arrayAttori;
  },
};
</script>

<style scoped lang="scss">
.flag {
  margin: 0.8rem auto;
  font-size: 2rem;
}
.card {
  height: 26rem;
  position: relative;
  width: 290px;
}
img {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 1312;
}
img:hover {
  opacity: 0;
  z-index: -1312;
}
.card:hover img {
  opacity: 0;
  z-index: -1312;
}
.star {
  font-size: 2rem;
  display: inline-block;
  color: gold;
}
.trama {
  position: absolute;
  z-index: 9000;
  background: black;
  border: 1px solid black;
  width: 15rem;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  padding: 1rem;
  width: 100%;
  overflow: auto;
}
.x {
  position: absolute;
  top: 0;
  right: 0;
  background-color: red;
  color: white;
}
.trama_button {
  background-color: red;
  color: white;
}
</style>
