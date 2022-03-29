<template>
  <div id="app">
    <Header-bool />
    <Main-bool />
  </div>
</template>

<script>
import HeaderBool from "./components/HeaderBool.vue";
import MainBool from "./components/MainBool.vue";

export default {
  name: "App",
  components: {
    HeaderBool,
    MainBool,
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";
</style>
