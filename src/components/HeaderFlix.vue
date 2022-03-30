<template>
  <header>
    <h1>Booflix</h1>
    <label for="searchBar">
      <input
        type="text"
        name="searchBar"
        v-model="stringValue"
        class=""
        @keyup.enter="$emit('ricerca', stringValue)"
      />
      <button @click="$emit('ricerca', stringValue)">Search</button>
    </label>
  </header>
</template>

<script>
export default {
  name: "HeaderFlix",
  data() {
    return {
      stringValue: "",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  padding-top: 2rem;
  background-color: black;

  h1 {
    color: red;
  }
}
</style>
