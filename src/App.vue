<template>
  <div id="app">
    <search-bar />
    <base-main />
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import BaseMain from './components/BaseMain.vue';

export default {
  name: "App",
  components: {
    SearchBar,
    BaseMain,
  },
};
</script>

<style lang="scss">
@import "./assets/style/global";
</style>
