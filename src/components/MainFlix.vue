<template>
  <main>
    <div class="container-cards">
      <CardFlix
        v-for="cardMovies in dataMovies"
        :key="cardMovies.id"
        :card-movies-data="cardMovies"
      />
    </div>
  </main>
</template>

<script>
import CardFlix from "../components/CardFlix.vue";

export default {
  name: "MainFlix",
  components: {
    CardFlix,
  },

  props: {
    dataMovies: Array,
  },
};
</script>

<style  scoped  lang="scss">
main {
  padding-top: 2rem;
  margin-left: 1rem;
  margin-right: 1rem;

  .container-cards {
    display: flex;
    flex-wrap: wrap;
  }
}
</style>
