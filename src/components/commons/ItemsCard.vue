<template>
  <ul class="item p-0 m-0 list-unstyled">
    <li>
      <h4>{{film.title}}</h4>
      <h4>{{film.name}}</h4>
      <h4>{{film.original_title}}</h4>
      <h4>{{film.original_name}}</h4>
      <img :src="getFlags(film.original_language)" :alt="film.original_language">
      <h4>{{film.vote_average}}</h4>
    </li>
  </ul>
</template>

<script>
import sharedData from '../shared/sharedData.js'

export default {
    name: 'ItemCard',
    props: {
        film: Object,
    },
    data() {
        return {
          sharedData
        }
    },
    methods: {
        getFlags(language) {
            if(language == "fr") {
                return this.sharedData.flags.fr;
            } else if(language == "ja") {
                return this.sharedData.flags.ja;
            } else if(language == "el") {
                return this.sharedData.flags.el;
            } else if(language == "sv") {
                return this.sharedData.flags.sv;
            } else if(language == "de") {
                return this.sharedData.flags.de;
            } else if(language == "us") {
                return this.sharedData.flags.us;
            } else if(language == "it") {
                return this.sharedData.flags.it;
            } else if(language == "es") {
                return this.sharedData.flags.es;
            } else {
                return this.sharedData.flags.en;
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    img {
        width: 20%;
    }
</style>