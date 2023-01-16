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
    <div class="left-part d-flex align-items-center">
      <div class="logo">
        <h1>Boolflix</h1>
      </div>
      <nav class="categories pt-3">
        <ul>
          <li>Home</li>
          <li>Serie TV</li>
          <li>Film</li>
        </ul>
      </nav>
    </div>

    <div class="search-part">
      <div class="search-bar">
        <i @click="searchInput = !searchInput" class="fa-solid fa-magnifying-glass"></i>
        <input v-show="searchInput" placeholder="Scrivi la tua ricerca" type="text" v-model="searchString">
      </div>
      <button class="btn btn-outline-light ms-2" @click="searchMovie(searchString), searchSeries(searchString)">Cerca</button>
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

    ul{
      list-style-type: none;
      li{
        display: inline-block;
        padding: 0 0.5rem;
        color: white;
      }
    }
  };
  .search-part{
    display: flex;
    align-items: center;
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
    .fa-paper-plane-top{
      font-size: 1.5rem;
      color: white;
    };

  }
</style>