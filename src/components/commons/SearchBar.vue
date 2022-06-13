<template>
  <div class="search_box">
    <form @submit.prevent="searching();searchingSeries()">
      <input type="text" v-model="searchItems" />
      <button type="submit" class="btn"><i class="fa-solid fa-magnifying-glass"></i></button>
    </form>
  </div>
</template>

<script>
import sharedData from "../shared/sharedData.js";
import axios from "axios";

export default {
  name: "SearchBar",
  data() {
    return {
      sharedData,
      searchItems: "",
    };
  },
  methods: {
    searching() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "b5d50dcfcc9b131150f732b632d34789",
            query: this.searchItems,
            language: "it-IT",
          },
        })
        .then((response) => {
          this.sharedData.films = response.data.results;
          this.searchItems = '';
        })
        .catch((error) => {
          console.log(error);
        });
    },
    searchingSeries() {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "b5d50dcfcc9b131150f732b632d34789",
            query: this.searchItems,
            language: "it-IT",
          },
        })
        .then((response) => {
          this.sharedData.series = response.data.results;
          this.searchItems = '';
        })
        .catch((error) => {
          console.log(error);
        });
    }
  },
};
</script>

<style lang="scss" scoped>
  form {
    display: flex;
    input {
      width: 100%;
      &:focus {
        outline: none;
      }
    }
    button {
      color: var(--text_color);
    }
}
</style>