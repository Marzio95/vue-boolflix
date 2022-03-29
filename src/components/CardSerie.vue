<template>
  <div class="card p-4 col-2 text-center text-white bg-black">
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
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
export default {
  name: "CardSerie",
  components: {
    LangFlag,
  },
  props: {
    serieData: Object,
  },
};
</script>

<style scoped lang="scss">
.flag {
  margin: 0.8rem auto;
  font-size: 2rem;
}
.card {
  height: 20rem;
}
</style>
