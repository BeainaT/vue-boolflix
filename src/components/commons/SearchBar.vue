<template>
  <div class="search_box">
    <form @submit.prevent="searching();searchingSeries();" class="justify-content-end">
      <input type="text" v-model="searchItems" />
      <button type="submit" class="btn">
        <i class="fa-solid fa-magnifying-glass"></i>
      </button>
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
  created() {
    axios.get("https://api.themoviedb.org/3/movie/popular", {
          params: {
            api_key: "b5d50dcfcc9b131150f732b632d34789",
            language: "it-IT",
          },
        })
        .then((response) => {
          this.sharedData.populars = response.data.results;
          console.log(response)
        })
        .catch((error) => {
          console.log(error);
        });
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
          this.searchItems = "";
          this.sharedData.populars = [];
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
          this.searchItems = "";
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  display: flex;

  &:hover input {
    width: 100%;
    padding: 0.125rem;
    outline: none;
  }

  input {
    width: 0;
    border: none;
    padding: 0;
    transition: 0.8s linear;
  }

  button,
  button:hover {
    color: var(--text_color);

    &:focus {
      outline: none;
    }
    
  }
}
</style>