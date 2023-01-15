<script>

import { store } from "../store";
import axios from 'axios';

export default {
  data() {
    return {
      store,
      searchText: "",
      apiSRC: "https://api.themoviedb.org/3/search/movie",
      apiKey: "7dadc080d7d03f1afb5d7530f5f79af4"

    }
  },
  methods: {
    getApi() {
      axios.get(this.apiSRC, {
        params: {
          api_key : this.apiKey,
          query : this.searchText,
        }
      })
        .then((response) =>{
          console.log(response.data.results);
          this.store.filmsList = response.data.results
          console.log(this.store.filmsList)
        })
        .catch(function (error) {
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    }
  },
}
</script>

<template>
  <header>
    <input type="text" v-model="searchText" @keyup.enter="getApi()">
    <div v-for="film in store.filmsList">{{film.title}}, {{film.original_title}}, {{film.original_language}}, {{film.vote_average}}</div>
  </header>
</template>

<style lang="">
  
</style>