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
        `movies`
      ]
    }
    </script>

<template>
  <div class="main-container">
    <section class="search-part">
      <input placeholder="Scrivi la tua ricerca" type="text" v-model="searchString">
      <button class="btn btn-primary ms-2" @click="$emit(`searchMovie`, searchString)">Clicca qui</button>
    </section>
  
    <section class="grid-results">
      <CardComponent v-for="movieElement in movies"
      :title="movieElement.title"
      :originalTitle="movieElement.original_title"
      :language="movieElement.original_language"
      :vote="movieElement.vote_average"
      />
    </section>
  </div>
</template>

<style lang="scss" scoped>
  
</style>