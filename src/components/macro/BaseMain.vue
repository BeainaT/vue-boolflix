<template>
  <main class="pb-4">

      <ul class="list-unstyled d-flex flex-wrap justify-content-center">
        <li class="px-2" v-for="genre in sharedData.genres" :key="genre.id"><a href="#">{{genre.name}}</a></li>
      </ul>

      <ItemSection/>
  </main>
</template>

<script>
import ItemSection from '../sections/ItemSection.vue';
import sharedData from '../shared/sharedData';
import axios from 'axios';

export default {
    name: 'BaseMain',
    components: {
        ItemSection,
    },
    data() {
        return {
            sharedData
        }
    },
    created() {
        axios.get("https://api.themoviedb.org/3/genre/movie/list", {
          params: {
            api_key: "b5d50dcfcc9b131150f732b632d34789",
            language: "it-IT",
          },
        })
        .then((response) => {
          this.sharedData.genres = response.data.genres;
        })
        .catch((error) => {
          console.log(error);
        });
    },
}
</script>

<style>

</style>