<template>
  <div class="card p-4 col-2 text-center text-white bg-black">
    <img
      v-show="serieData.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342/' + serieData.poster_path"
      :alt="serieData.title"
    />
    <h2>{{ serieData.name }}</h2>
    <h3
      v-show="
        serieData.name.toLowerCase() != serieData.original_name.toLowerCase()
      "
    >
      {{ serieData.original_name }}
    </h3>
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
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "CardSerie",
  data() {
    return {
      starf: "star",
      arrayStars: [],
      stars: Math.floor(this.serieData.vote_average / 2),
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
      console.log(this.stars);
      return this.stars;
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
  height: 23rem;
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
