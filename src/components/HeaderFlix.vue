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

<style scoped lang="scss"></style>
