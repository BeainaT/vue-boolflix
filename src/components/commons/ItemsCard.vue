<template>
  <ul class="item p-0 m-0 list-unstyled">
    <li class="img_box">
        <img class="poster_item" :src="getPoster(film.poster_path)" alt="film poster">
        <div class="descriptions_item">
            <p>{{film.title}}</p>
            <p>{{film.name}}</p>
            <p>{{film.original_title}}</p>
            <p>{{film.original_name}}</p>
            <p>{{film.vote_average}}</p>
            <lang-flag :iso="film.original_language" :alt="film.original_language"/>
        </div>
    </li>
  </ul>
</template>

<script>
import sharedData from '../shared/sharedData.js'
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'ItemCard',
    props: {
        film: Object,
    },
    components: {
        LangFlag,
    },
    data() {
        return {
          sharedData,
        }
    },
    methods: {
        getPoster(path) {
            return path == null ? 'https://moviereelist.com/wp-content/uploads/2019/07/poster-placeholder.jpg' : 'https://image.tmdb.org/t/p/w342'+path;
        }
    }
}
</script>

<style lang="scss" scoped>
    .img_box {
        position: relative;
            .poster_item {
                width: 100%;
            }
            .descriptions_item {
                height: 100%;
                width: 100%;
                position: absolute;
                top: 0;
                left: 0;
                color: #fff;
                background-color: rgba($color: #000000, $alpha: 0.9);
                opacity: 0;
                &:hover {
                    opacity: 1;
                    transition: 0.5s linear;
                }
                .flag-icon-undefined {
                    width: 1.25rem;
                    height: auto;
                    background-image: url(https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/World_Flag_%282004%29.svg/2560px-World_Flag_%282004%29.svg.png);
                    background-size: cover;
                }
            }

    }

</style>