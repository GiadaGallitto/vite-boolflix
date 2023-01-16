    <script>
    import CardComponent from "./CardComponent.vue"

    export default {
      components : {
        CardComponent
      },
      
      data(){
        return{
          searchString : "",
        }
      },

      props: [
        `movies`,
        `series`
      ],

      methods: {
        searchMovie(string){
          this.$emit(`searchMovie`, string)
        },

        searchSeries(string){
          this.$emit(`searchSeries`, string)
        }
      }
    }
    </script>

<template>
  <div class="main-container">
    <section class="search-part">
      <input placeholder="Scrivi la tua ricerca" type="text" v-model="searchString">
      <button class="btn btn-primary ms-2" @click="searchMovie(searchString), searchSeries(searchString)">Clicca qui</button>
    </section>
  
    <section class="grid-results">
      <CardComponent v-for="movieElement in movies"
      :title="movieElement.title"
      :originalTitle="movieElement.original_title"
      :language="movieElement.original_language"
      :vote="Math.ceil(movieElement.vote_average)"
      :cover="movieElement.poster_path"
      />
      <CardComponent v-for="serieElement in series"
      :title="serieElement.name"
      :originalTitle="serieElement.original_name"
      :language="serieElement.original_language"
      :vote="Math.ceil(serieElement.vote_average)"
      :cover="serieElement.poster_path"
      />
    </section>
  </div>
</template>

<style lang="scss" scoped>
  
</style>