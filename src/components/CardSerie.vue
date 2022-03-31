<template>
  <div class="card p-4 col-2 text-center text-white bg-black">
    <img
      v-if="serieData.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342/' + serieData.poster_path"
      :alt="serieData.title"
    />
    <h3>{{ serieData.name }}</h3>
    <h5
      v-show="
        serieData.name.toLowerCase() != serieData.original_name.toLowerCase()
      "
    >
      {{ serieData.original_name }}
    </h5>
    <lang-flag
      class="flag"
      :iso="serieData.original_language"
      :squared="false"
    />
    <h4>{{ serieData.vote_average }}</h4>
    <div>
      <div class="star" v-for="element in fullArrayStars()" :key="element">
        &starf;
      </div>
    </div>
    <div
      class="actor"
      v-for="element in ricercaAttori /*()*/"
      :key="element.name"
    >
      {{ element.name }}
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
import axios from "axios";

export default {
  name: "CardSerie",
  data() {
    return {
      starf: "star",
      arrayStars: [],
      stars: Math.round(this.serieData.vote_average / 2),
      arrayAttori: null,
    };
  },
  components: {
    LangFlag,
  },
  props: {
    serieData: Object,
  },
  methods: {
    fullArrayStars() {
      return this.stars;
    },
    ricercaAttori() {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${this.serieData.id}/credits?api_key=9631e84004e35c8371fcb3c009af9551`
        )
        .then((response) => {
          this.arrayAttori = response.data.cast;
        });
      this.arrayAttori.length = 5;
      console.log(this.arrayAttori);
      return this.arrayAttori;
    },
  },
};
</script>

<style scoped lang="scss">
.flag {
  margin: 0.8rem auto;
  font-size: 2rem;
}
.card {
  height: 25rem;
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
  transition: 1s;
  opacity: 0;
}
.star {
  font-size: 2rem;
  display: inline-block;
  color: gold;
}
</style>
