<template>
    <section  class="container">
        <div>
            <div class="row gap-3 justify-content-center">
                    <div class="col-12 col-md-3 col-lg-2" v-for="popular in filteredGenres" :key="popular.id">
                        <ItemsCard :film="popular" />
                    </div>                    
                <template v-if="filteredGenres.length < 1 && sharedData.films.length < 1">
                    <div class="py-3 text-center">
                        <h3>Siamo spiacenti</h3>
                        <h5>Non ci sono al momento titoli per {{notFound() ? "questo genere" : "questa ricerca"}}</h5>
                    </div>
                </template>
                <div class="col-12 col-md-3 col-lg-2" v-for="film in sharedData.films" :key="film.id">
                    <ItemsCard :film="film"/>
                </div>
                <div class="col-12 col-md-3 col-lg-2" v-for="serie in sharedData.series" :key="serie.id">
                    <ItemsCard :film="serie"/>
                </div>
            </div>
        </div>
    </section>

</template>

<script>
import ItemsCard from "../commons/ItemsCard.vue";
import sharedData from "../shared/sharedData.js";

export default {
    name:'ItemSection',
    components: {
        ItemsCard,
    },
    props: {
        genreId: Number
    },
    data() {
        return {
            sharedData,
        }
    },
    methods: {
        notFound() {
            if(this.sharedData.populars.length !== 0) {
                return true
            } else {
                return false
            }
        },
    },
    computed: {
        filteredGenres() {
            if(this.genreId == null) {
                return this.sharedData.populars;
            } else {
                let filter = this.sharedData.populars.filter(elm => {
                    return elm.genre_ids.includes(this.genreId);
                });
                return filter;          
            }
        }
    },
}
</script>

<style lang="scss" scoped>
    .main_container {
        text-align: center;
        ul {
            list-style: none;
        }
    }

</style>