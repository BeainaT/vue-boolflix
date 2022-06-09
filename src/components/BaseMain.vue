<template>
    <div class="main_container">
        <ul>
            <li v-for="film in films" :key="film.id">{{film.original_title}}</li>
        </ul>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name:'BaseMain',
    props: {
        film: String,
    },
    data() {
        return {
            films: [],
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: 'b5d50dcfcc9b131150f732b632d34789',
                query: 'hello',
                language: 'it-IT'
            }
        }) 
            .then((response)=> {
                this.films = response.data.results
            })
            .catch((error)=> {
                console.log(error)
            })
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