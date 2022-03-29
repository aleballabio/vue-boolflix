<template>
  <div id="app">
    <HeaderFlix />
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
    return {};
  },

  methods: {},

  computed: {},
};
</script>

<style lang="scss">
@import "./assets/style.scss";

#app {
}
</style>
