<template>
  <main>
    <h1 v-show="search !== ''">Film</h1>
    <h2 v-show="search != ''" v-if="dataMovies.length < 1">
      Non ci sono risultati
    </h2>

    <div class="container-cards">
      <CardFlix v-for="card in dataMovies" :key="card.id" :card-data="card" />
    </div>

    <h1 v-show="search != ''">Serie TV</h1>
    <h2 v-show="search != ''" v-if="dataSeries.length < 1">
      Non ci sono risultati
    </h2>

    <div class="container-cards">
      <CardFlix v-for="card in dataSeries" :key="card.id" :card-data="card" />
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
    dataSeries: Array,
    search: String,
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
    align-items: center;
  }

  h1 {
    color: white;
    padding-bottom: 1rem;
    padding-top: 1rem;
  }

  h2 {
    color: rgb(173, 173, 173);
  }
}
</style>
