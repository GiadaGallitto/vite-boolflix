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
      },
      methods: {
        getImagePath: function (img) {
          return new URL(`../assets/flag-img/${img}.png`, import.meta.url).href;
        },
        getImageCover()
      },

      }
    </script>

<template>
  <div class="card">
    <img :src="" alt="">
    <h3>{{ title }}</h3>
    <h5>{{ originalTitle }}</h5>
    <img :src="getImagePath(language)" >
    <span>{{ vote }}</span>
  </div>
</template>

<style lang="scss">
  img{
    width: 10%;
  }
</style>