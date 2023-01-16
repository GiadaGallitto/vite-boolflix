    <script>
    import { store } from "../store.js";
    import axios from "axios";

    export default {
      data(){
        return {
          store,
          flag: ""
        }
      },

      props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: String,
        cover: String
      },
      methods: {
        getImagePath: function (img) {
          return new URL(`../assets/flag-img/${img}.png`, import.meta.url).href;
        }
      },

      }
    </script>

<template>
  <div class="card">
    <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${cover}`" alt="">
    <h3>{{ title }}</h3>
    <h5>{{ originalTitle }}</h5>
    <img class="flag" :src="getImagePath(language)" >
    <span>{{ vote }}</span>
  </div>
</template>

<style lang="scss">
  .poster{
    width: 20%
  };
  .flag{
    width: 5%;
  }
</style>