    <script>
    export default {
      data(){
        return{
          searchString : "",
          searchInput: false,
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
      <div class="search-bar">
        <i @click="searchInput = !searchInput" class="fa-solid fa-magnifying-glass"></i>
        <input v-show="searchInput" placeholder="Scrivi la tua ricerca" type="text" v-model="searchString">
      </div>
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
  };
  .search-part{
    display: flex;
    .search-bar{
      display: inline-block;
      .fa-magnifying-glass{
        font-size: 1.5rem;
        color: white;
        margin-right: 1rem;
      };

      input{
        padding: 0.3rem 0;
      }
    }
  }
</style>