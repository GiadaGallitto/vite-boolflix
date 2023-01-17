    <script>
    import CardComponent from "./CardComponent.vue"

    export default {
      components : {
        CardComponent
      },
      
      data(){
        return{

        }
      },

      props: [
        `movies`,
        `series`
      ],

    }
    </script>

<template>
  <div class="main-container">
    <section class="grid-results row">
      <h2 class="col-12">Film:</h2>
      <CardComponent class="col-10 col-md-3 col-sm-4 col-lg-2" v-for="movieElement in movies"
      :title="movieElement.title"
      :originalTitle="movieElement.original_title"
      :language="movieElement.original_language"
      :vote="Math.ceil(movieElement.vote_average)"
      :cover="movieElement.poster_path"
      :overview="movieElement.overview"
      :genreIds="movieElement.genre_ids"
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