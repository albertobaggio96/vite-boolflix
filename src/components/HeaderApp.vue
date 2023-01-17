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
        })
        .catch(function (error) {
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    },

    giveApiKeyToStore(){
      this.store.apiKey = this.apiKey
    }
  },
  created(){
    this.giveApiKeyToStore()
  }
}
</script>

<template>
  <header class="bg-black py-4 d-flex align-items-center">
    <h1 class="text-danger ps-3 me-auto">BOOLFIX</h1>
    <div class="pe-3 d-flex">
      <input type="text" v-model="searchText" @keyup.enter="getApi()" class="me-2 form-control">
      <button @click="getApi()" class="btn btn-light">Cerca</button>
    </div>
  </header>
</template>

<style lang="">
  
</style>