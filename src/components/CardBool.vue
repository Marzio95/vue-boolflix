<template>
  <div class="card col-2 text-center">
    <h1>{{ filmData.title }}</h1>
    <h2>{{ filmData.original_title }}</h2>
    <h3>{{ filmData.original_language }}</h3>
    <h4>{{ filmData.release_date }}</h4>
  </div>
</template>

<script>
export default {
  name: "CardBool",
  props: {
    filmData: Object,
  },
};
</script>

<style scoped lang="scss"></style>
