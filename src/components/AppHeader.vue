    <script>
    export default {
      data(){
        return{
          searchString : "",
        }
      },

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
  <section class="header-part">
    <div class="logo">
      <h1>Boolflix</h1>
    </div>

    <div class="search-part">
      <input placeholder="Scrivi la tua ricerca" type="text" v-model="searchString">
      <button class="btn btn-primary ms-2" @click="searchMovie(searchString), searchSeries(searchString)">Clicca qui</button>
    </div>
  </section>


</template>

<style lang="scss" scoped>
  .header-part{
    padding: 0.8rem 1rem;
    background-color: rgb(0, 0, 0);
    display: flex;
    justify-content: space-between;
    align-items: center;
    
    h1{
      font-size: 2rem;
      color: red;
    }
  }
</style>