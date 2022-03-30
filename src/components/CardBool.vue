<template>
  <div class="card p-4 col-2 text-center text-white bg-black">
    <img
      v-show="filmData.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342/' + filmData.poster_path"
      :alt="filmData.title"
    />
    <h3>{{ filmData.title }}</h3>
    <h5
      v-show="
        filmData.title.toLowerCase() != filmData.original_title.toLowerCase()
      "
    >
      {{ filmData.original_title }}
    </h5>
    <lang-flag class="flag" :iso="filmData.original_language" squared="false" />
    <h4>{{ filmData.vote_average }}</h4>
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
  name: "CardBool",
  data() {
    return {
      starf: "star",
      arrayStars: [],
      stars: Math.floor(this.filmData.vote_average / 2),
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
