<template>
    <section>
        <div class="container">
            <div class="row">
                <div class="col-12 col-md-3" v-for="film in sharedData.films" :key="film.id">
                    <ItemsCard :film="film"/>
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