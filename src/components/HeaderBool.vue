<template>
  <header class="header p-4">
    <h1>Boolflix</h1>
    <div>
      <input type="text" name="film" id="film" placeholder="Cerca film" />
      <button>Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderBool",
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
