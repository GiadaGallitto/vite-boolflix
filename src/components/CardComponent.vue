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
        getFlag(lang){
          const apiUrl = (lang == "" || lang == "en") ? `https://countryflagsapi.com/png/gb` : `https://countryflagsapi.com/png/${lang}`
          axios.get(apiUrl, {
                    params: {
                        
                    }
                })
                .then((response) => {
                    console.log(response);
                    this.flag = apiUrl
                    console.log(this.flag)
                })
                .catch(function (error) {
                    console.log(error);
                })
            }
          // getFlag(lang) {
          //   const apiUrl = (lang == "en") ? `https://countryflagsapi.com/png/gb` : `https://countryflagsapi.com/png/${lang}`
          //   this.flag = apiUrl
          //   console.log(this.flag)
          // }
        },

        created(){
          this.getFlag(this.language)
        }
      }
    </script>

<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <h5>{{ originalTitle }}</h5>
    <img :src="flag" >
    <span>{{ vote }}</span>
  </div>
</template>

<style lang="scss">
  
</style>