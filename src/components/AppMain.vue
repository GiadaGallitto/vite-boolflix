    <script>
    import CardComponent from "./CardComponent.vue"
    import  { store } from "../store.js"
    import axios from "axios";

    export default {
      components : {
        CardComponent
      },
      
      data(){
        return{
          store,
        }
      },

      props: [
        `movies`,
        `series`
      ],

      methods: {
        getGenres(){
          const urlApi = `https://api.themoviedb.org/3/genre/movie/list?api_key=d5997a9a3f571aa73cf4c8a72523ddf2&language=en-US`
                axios.get(urlApi, {
                    params: {

                    }
                })
                .then((response) => {
                    console.log(response.data.genres);
                    this.store.genresList = response.data.genres
                    console.log(this.store.genresList)
                })
                .catch(function (error) {
                    console.log(error);
                })

        },

        getActors(){

        }
      },

      created(){
        this.getGenres();
      }

    }
    </script>

<template>
  <div class="main-container">
    <section class="grid-results row">
      <h2 class="col-12">Film:</h2>
      <CardComponent class="col-10 col-md-3 col-sm-4 col-lg-2" v-for="(movieElement, index) in movies"
      :index="index"
      :title="movieElement.title"
      :originalTitle="movieElement.original_title"
      :language="movieElement.original_language"
      :vote="Math.ceil(movieElement.vote_average)"
      :cover="movieElement.poster_path"
      :overview="movieElement.overview"
      :genreIds="movieElement.genre_ids"
      :personalId="movieElement.id"
      />
      <h2 class="col-12">Serie Tv:</h2>
      <CardComponent class="col-10 col-md-3 col-sm-4 col-lg-2" v-for="serieElement in series"
      :title="serieElement.name"
      :originalTitle="serieElement.original_name"
      :language="serieElement.original_language"
      :vote="Math.ceil(serieElement.vote_average)"
      :cover="serieElement.poster_path"
      :overview="serieElement.overview"
      :genreIds="serieElement.genre_ids"
      :personalId="serieElement.id"
      />
    </section>
  </div>
</template>

<style lang="scss" scoped>
  .main-container{
    width: 90%;
    margin: 2rem auto;
  }
  .grid-results{
    // display: flex;
    // flex-wrap: wrap;

    h2{
      color: white;
    }
  }
</style>