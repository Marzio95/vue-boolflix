<template>
  <main class="p-5">
    <div class="full_screen" v-if="arrayFilms == null">Cerca un Film</div>
    <div v-else class="container">
      <h3 class="text-center mb-4">films</h3>
      <div class="row gap-3 flexbox">
        <Card-bool
          v-for="element in arrayFilms"
          :key="element.id"
          :film-data="element"
        />
      </div>
    </div>
  </main>
</template>

<script>
import CardBool from "./CardBool.vue";
export default {
  components: { CardBool },
  name: "MainBool",
  data() {
    return {};
  },
  props: {
    arrayFilms: Array,
  },
};
</script>

<style scoped lang="scss">
main {
  background-color: grey;
}
.flexbox {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.full_screen {
  height: calc(100vh - 200px);
  background-color: grey;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
  text-transform: uppercase;
  font-weight: 700;
}
h3 {
  font-size: 3rem;
  text-transform: uppercase;
}
</style>
