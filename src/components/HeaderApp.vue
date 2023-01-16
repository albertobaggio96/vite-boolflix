<script>

import { store } from "../store";
import axios from 'axios';

export default {
  name: "HeaderApp",
  data() {
    return {
      store,
      searchText: "",
      apiMovieURL: "https://api.themoviedb.org/3/search/movie",
      apiTVShowURL: "https://api.themoviedb.org/3/search/tv",
      apiKey: "7dadc080d7d03f1afb5d7530f5f79af4"

    }
  },
  methods: {
    getApi() {
      axios.get(this.apiMovieURL, {
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
      
        axios.get(this.apiTVShowURL, {
        params: {
          api_key : this.apiKey,
          query : this.searchText,
        }
      })
        .then((response) =>{
          console.log(response.data.results);
          this.store.TVShowList = response.data.results
          console.log(this.store.TVShowList)
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
  </header>
</template>

<style lang="">
  
</style>