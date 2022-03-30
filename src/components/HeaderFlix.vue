<template>
  <header>
    <h1>Booflix</h1>
    <label for="searchBar">
      <input
        type="text"
        name="searchBar"
        v-model="stringValue"
        class="input-search"
        @keyup.enter="$emit('ricerca', stringValue)"
      />
      <button id="button-search" @click="$emit('ricerca', stringValue)">
        Search
      </button>
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

  #button-search {
    margin-left: 1rem;
    padding: 2px;
    padding-left: 5px;
    padding-right: 5px;
  }
}
</style>
