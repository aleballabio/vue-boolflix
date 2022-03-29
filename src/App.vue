<template>
  <div id="app">
    <HeaderFlix @ricerca="setValue" />
    <MainFlix />
  </div>
</template>

<script>
import HeaderFlix from "./components/HeaderFlix";
import MainFlix from "./components/MainFlix";
//import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderFlix,
    MainFlix,
  },

  data() {
    return {
      nameToSearch: "",
    };
  },

  methods: {
    setValue(value) {
      this.nameToSearch = value;
      console.log(value);
      console.log(this.nameToSearch);
    },
  },
  // Importazione Chiave AXios

  // https://api.themoviedb.org/3/search/movie?api_key=QUILATUAKEY&language=it-IT&query=QUILASTRINGADIRICERCA
  // axios.get('https://api.themoviedb.org/3/search/movie?api_key=QUILATUAKEY&query=' + nomevariabile)

  computed: {},
};
</script>

<style lang="scss">
@import "./assets/style.scss";

#app {
}
</style>
