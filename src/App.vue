<script>
    import AppHeader from "./components/AppHeader.vue";
    import AppMain from "./components/AppMain.vue";
    import { store } from "./store.js";
    import axios from "axios";

    export default{
        data(){
            return{
                store,
            }
        },

        components: {
            AppHeader,
            AppMain,
        },

        methods: {
            getMovie(searchedMovie = "ritorno al futuro"){
                const urlApi = `https://api.themoviedb.org/3/search/movie`
                axios.get(urlApi, {
                    params: {
                        api_key : 'd5997a9a3f571aa73cf4c8a72523ddf2',
                        query : searchedMovie
                    }
                })
                .then((response) => {
                    console.log(response.data.results);
                    this.store.movieList = response.data.results;
                    console.log(this.store.movieList)
                })
                .catch(function (error) {
                    console.log(error);
                })
            }
        },

        created (){
            this.getMovie();
        }
    }
</script>

<template>
    <div>
        <header>
            <AppHeader />
        </header>

        <main>
            <AppMain :movies="store.movieList" @searchMovie="getMovie" />
        </main>
    </div>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>
