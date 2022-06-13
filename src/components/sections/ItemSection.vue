<template>
    <section  class="container">
        <div>
            <div class="row gap-3 justify-content-center">
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
    data() {
        return {
            sharedData,            
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