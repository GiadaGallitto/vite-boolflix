    <script>
    import { store } from "../store.js";
    import axios from "axios";

    export default {
      data(){
        return {
          store,
          presentFlags: ["de", "en", "fr", "it", "ja"],
          fullStars: [],
          emptyStars: [],
          newGenresList: [],
          hover: false,

        }
      },

      props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        cover: String,
        overview: String,
        genreIds: Array,
        personalId: Number
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
        },

        showGenres(){
          console.warn('lunghezza:' , this.store.genresList.length);


          this.store.genresList.forEach(genre => {
              if (this.genreIds.includes(genre.id)){
                this.newGenresList.push(genre.name)
              }
          });
          console.log('GENERI', this.newGenresList)

        },

        getActor(numId){
          const urlApi = `https://api.themoviedb.org/3/movie/${numId}/credits?api_key=d5997a9a3f571aa73cf4c8a72523ddf2`
                axios.get(urlApi, {
                    params: {

                    }
                })
                .then((response) => {
                    console.log(response.data.cast);
                    for(let i=0; i < 5; i++){
                      this.store.actorsList.push(response.data.cast[i].name)
                    }
                    console.log(this.store.actorsList)
                })
                .catch(function (error) {
                    console.log(error);
                })
        }

      },

      created() {
        this.getStarsVote(this.vote);
        // this.getActor();

        setTimeout(this.showGenres, 1000);
      }

      }
    </script>

<template>
  <div class="card-element" @mouseover="hover = true" @mouseleave="hover = false">
    <img v-if="cover != null" class="poster" :src="`https://image.tmdb.org/t/p/w342/${cover}`" alt="">
    <img v-else class="poster" src="../assets/default-movie.jpg" alt="default img">
    <div  class="info">
      <ul>
        <li><h6>Titolo: </h6>{{ title }}</li>
        <li v-if="title != originalTitle"><h6>Titolo originale: </h6>{{ originalTitle }}</li>
        <li>
          <img v-if="presentFlags.includes(language)" class="flag" 
          :src="getImagePath(language)" >
          <span v-else ><h6> Lingua: </h6>{{ language }}</span>
        </li>
        <li><h6>Voto: </h6>        
          <div class="stars d-inline">
            <i v-for="starEL in fullStars" class="fa-solid fa-star"></i>
            <i v-for="star in emptyStars" class="fa-regular fa-star"></i>
          </div>
        </li>
        <li><h6>Overview: </h6>{{ overview }}</li>
        <li><h6>Generi: </h6> 
          <span v-for="genreElement in newGenresList"> {{ genreElement }}, </span>
        </li>
        <li><h6>Attori: </h6>{{ getActor(personalId) }}</li>
      </ul>
    </div>

  </div>
</template>

<style lang="scss" scoped>
  .card-element{
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