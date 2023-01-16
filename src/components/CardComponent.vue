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

      }
    </script>

<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <h5>{{ originalTitle }}</h5>
    <img :src="`../assets/flag-img/${language}.png`" >
    <span>{{ vote }}</span>
  </div>
</template>

<style lang="scss">
  
</style>