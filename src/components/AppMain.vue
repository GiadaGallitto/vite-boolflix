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
      <CardComponent v-for="movieElement in movies"
      :title="movieElement.title"
      :originalTitle="movieElement.original_title"
      :language="movieElement.original_language"
      :vote="Math.ceil(movieElement.vote_average)"
      :cover="movieElement.poster_path"
      :overview="movieElement.overview"
      />
      <CardComponent v-for="serieElement in series"
      :title="serieElement.name"
      :originalTitle="serieElement.original_name"
      :language="serieElement.original_language"
      :vote="Math.ceil(serieElement.vote_average)"
      :cover="serieElement.poster_path"
      :overview="serieElement.overview"
      />
    </section>
  </div>
</template>

<style lang="scss" scoped>
  .main-container{
    width: 90%;
    height: 1000px;
    margin: 2rem auto;
  }
  .grid-results{
    display: flex;
    flex-wrap: wrap;
  }
</style>