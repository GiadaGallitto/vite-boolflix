    <script>
    import { store } from "../store.js";
    import axios from "axios";

    export default {
      data(){
        return {
          store,
          fullStars: [],
          emptyStars: [],
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
        },

        getStarsVote(num){
          let fullStarElement = Math.ceil(num / 2)
          console.log(num)
          console.log(fullStarElement)

          for(let i = 0; i < fullStarElement ; i++){
            this.fullStars.push(fullStarElement);
          }
          console.log(this.fullStars.length)

          let emptyStarElement = 1
          for(let i = 0; i < (5 - this.fullStars.length) ; i++){
            this.emptyStars.push(emptyStarElement)
          }
          console.log(this.emptyStars.length)
        }
      },

      created() {
        this.getStarsVote(this.vote)
      }

      }
    </script>

<template>
  <div class="card">
    <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${cover}`" alt="">
    <h3>{{ title }}</h3>
    <h5>{{ originalTitle }}</h5>
    <img class="flag" :src="getImagePath(language)" >
    <div class="stars">
      <i v-for="starEL in fullStars" class="fa-solid fa-star"></i>
      <i v-for="star in emptyStars" class="fa-regular fa-star"></i>
    </div>
  </div>
</template>

<style lang="scss">
  .poster{
    width: 20%
  };
  .flag{
    width: 5%;
  };
  .stars i{
    color: rgb(194, 194, 11);
  }
</style>