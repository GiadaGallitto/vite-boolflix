    <script>
    import { store } from "../store.js";
    import axios from "axios";

    export default {
      data(){
        return {
          store,
          fullStars: [],
          emptyStars: [],
          hover: false
        }
      },

      props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: String,
        cover: String,
        overview: String
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
  <div class="card-element col-4" @mouseover="hover = true" @mouseleave="hover = false">
    <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${cover}`" alt="">

    <div v-if="hover" class="info">
      <ul>
        <li><h6>Titolo: </h6>{{ title }}</li>
        <li v-if="title != originalTitle"><h6>Titolo originale: </h6>{{ originalTitle }}</li>
        <li><img class="flag" :src="getImagePath(language)" ></li>
        <li><h6>Voto: </h6>        
          <div class="stars d-inline">
            <i v-for="starEL in fullStars" class="fa-solid fa-star"></i>
            <i v-for="star in emptyStars" class="fa-regular fa-star"></i>
          </div>
        </li>
        <li><h6>Overview: </h6>{{ overview }}</li>
      </ul>
    </div>

  </div>
</template>

<style lang="scss" scoped>
  .card-element{
    width: calc((100% / 5) - 3rem);
    margin: 1.5rem 1.5rem;
    color: white;
    position: relative;
    // aspect-ratio: ;
    .poster{
      width: 100%;
      height: 100%;
    };

    .info{
      background-color: rgba(0, 0, 0, 0.8);
      height: 100%;
      margin: 0 0.7rem;
      padding: 1.5rem 0;
      overflow: auto;
      position: absolute;
      top: 0;
      left: 0;

      ul{
        list-style-type: none;
        li{
          padding-right: 1.5rem;
          font-weight: 200;
          h6{
            display: inline;
            font-size: 1rem;
          }
        }
      }
      .flag{
        width: 20%;
      };
  
      .stars i{
        color: rgb(194, 194, 11);
      }
    }
  }
</style>