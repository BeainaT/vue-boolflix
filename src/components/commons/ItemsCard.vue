<template>
  <ul class="item p-0 m-0 list-unstyled">
    <li class="img_box" @mouseenter="showDetails()" @mouseleave="showDetails()">
        <img class="poster_item" :src="getPoster(film.poster_path)" alt="film poster">
        <transition>
            <div class="descriptions_item py-4 px-2 py-3" v-if="(visible)">
                <p><strong>Titolo:</strong>{{film.title || film.name}}</p>
                <p><strong>Titolo originale:</strong>{{film.original_title || film.original_name}}</p>
                <div class="vote">
                    <strong>Voto:</strong>
                    <i class="fa-solid fa-star" v-for="(star, i) in getStars(film.vote_average)" :key="'star' + i"></i>
                    <i class="fa-regular fa-star" v-for="(emptyStar, i) in 5 - getStars(film.vote_average)" :key="'emptyStar' + i"></i>
                </div>
                <lang-flag :iso="film.original_language" :alt="film.original_language" class="d-block"/>
                <p><strong>Trama:</strong>{{getOverview(film.overview)}}</p>
            </div>
        </transition>
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
          visible: false,
        }
    },
    methods: {
        getPoster(path) {
            return path == null ? 'https://moviereelist.com/wp-content/uploads/2019/07/poster-placeholder.jpg' : 'https://image.tmdb.org/t/p/w342'+path;
        },
        getStars(elm) {
            return Math.ceil((elm / 2));
        },
        getOverview(elm) {
            return elm === "" ? `Sorry, no plot available for this item` : elm;
        },
        showDetails() {
            return this.visible = !this.visible;
        }
    },
}
</script>

<style lang="scss" scoped>
    .img_box {
        position: relative;
            .poster_item {
                width: 100%;
            }
            .v-enter-active,
            .v-leave-active {
                transition: opacity 0.8s linear;
            }
            .v-enter,
            .v-leave-to {
                opacity: 0 ;
            }
            .descriptions_item {
                height: 100%;
                width: 100%;
                position: absolute;
                top: 0;
                left: 0;
                color: #fff;
                background-color: rgba($color: #000, $alpha: 0.9);
                overflow-y: auto;
                &::-webkit-scrollbar {
                    width: .625rem;
                }
                &::-webkit-scrollbar-track {
                    background-color: var(--secondary_color);
                    border-radius: 6.25rem; 
                }
                &::-webkit-scrollbar-thumb {
                    border-radius: 6.25rem;
                    border: .0625rem solid var(--text_color);
                    background-color: var(--primary_color);
            }       
                .flag-icon-undefined {
                    width: 1.25rem;
                    height: auto;
                    background-image: url(https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/World_Flag_%282004%29.svg/2560px-World_Flag_%282004%29.svg.png);
                    background-size: cover;
                }
                > * {
                    margin: 0;
                }
            }
    }

</style>