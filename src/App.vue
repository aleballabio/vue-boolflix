<template>
  <div id="app">
    <HeaderFlix @ricerca="setValue" />
    <MainFlix
      :data-movies="movies"
      :data-series="series"
      :search="nameToSearch"
    />
    <link
      rel="stylesheet"
      href="bower_components/css-star-rating/dist/css/star-rating.css"
    />
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
      series: [],
      nameToSearch: "",
      urlToSearchMovie:
        "https://api.themoviedb.org/3/search/movie?&language=it-IT&api_key=31db468853f5bed222bea1c794738e59&query=",
      urlToSearchSeries:
        "https://api.themoviedb.org/3/search/tv?&language=it-IT&api_key=31db468853f5bed222bea1c794738e59&query=",
    };
  },

  methods: {
    setValue(value) {
      this.nameToSearch = value;
      this.searching = true;
      if (this.nameToSearch !== "") {
        axios
          .get(this.urlToSearchMovie + this.nameToSearch)
          .then((response) => {
            this.movies = response.data.results;
          });

        (this.series = []),
          axios
            .get(this.urlToSearchSeries + this.nameToSearch)
            .then((response) => {
              this.series = response.data.results;
            });
      } else {
        this.movies = [];
        this.series = [];
      }
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style.scss";

#app {
}
</style>
