<template>
  <div id="app">
    <HeaderFlix @ricerca="setValue" />
    <MainFlix :data-movies="movies" />
  </div>
</template>

<script>
import HeaderFlix from "./components/HeaderFlix";
import MainFlix from "./components/MainFlix";
import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderFlix,
    MainFlix,
  },

  data() {
    return {
      movies: [],
      nameToSearch: null,
      urlToSearchMovie:
        "https://api.themoviedb.org/3/search/movie?api_key=31db468853f5bed222bea1c794738e59&query=",
      urlToSearchSeries:
        "https://api.themoviedb.org/3/search/movie?api_key=31db468853f5bed222bea1c794738e59&query=",
    };
  },

  methods: {
    setValue(value) {
      this.nameToSearch = value;
      console.log(value);
      (this.movies = []),
        axios
          .get(
            "https://api.themoviedb.org/3/search/movie?api_key=31db468853f5bed222bea1c794738e59&query=" +
              this.nameToSearch
          )
          .then((response) => {
            this.movies = response.data.results;
          });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style.scss";

#app {
}
</style>
