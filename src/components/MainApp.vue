<script>

import { store } from "../store";

import FilmApp from "./main-components/FilmsApp.vue"
import TVSeriesApp from "./main-components/TVSeriesApp.vue"

export default {
  name: "MainApp",
  components:{
    FilmApp,
    TVSeriesApp,
  },
  data(){
    return{
      store,
      flagsAvailable: ["de", "en", "es", "fi", "fr", "it", "ja", "ko", "pl", "zh"]
    }
  },
  methods:{
    
  },
}
</script>

<template>
  <main>
    <h1>Film</h1>

    <article v-for="film in store.filmsList">
      <FilmApp :film="film" :flagsAvailable="flagsAvailable"/>
    </article>

    <h1>TV series</h1>

    <article v-for="TVShow in store.TVShowList">
      <TVSeriesApp :TVShow="TVShow" :flagsAvailable="flagsAvailable"/>
    </article>

  </main>
</template>

<style lang="scss">
  img{
    width: 30px;
  }
</style>