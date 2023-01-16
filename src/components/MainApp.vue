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
    getImgPath(imgPath){
      imgPath = this.flagsAvailable.includes(imgPath) ? imgPath : "rainbow";
      return new URL(`../assets/img/${imgPath}.png`, import.meta.url).href;
    },
    isFlagAvailable(imgPath){
      this.getImgPath (imgPath);
    }
  },
}
</script>

<template>
  <main>
    <h1>Film</h1>

    <article v-for="film in store.filmsList">
      <FilmApp  
        :title="film.title" 
        :originalTitle="film.original_title" 
        :originalLanguageFlag="getImgPath(film.original_language)"
        :originalLanguage="film.original_language"
        :voteAverage="film.vote_average"
        :posterPath="film.poster_path"/>
    </article>

    <h1>TV series</h1>

    <article v-for="TVShow in store.TVShowList">
      <TVSeriesApp 
        :title="TVShow.name" 
        :originalTitle="TVShow.original_name" 
        :originalLanguageFlag="getImgPath(TVShow.original_language)"
        :originalLanguage="TVShow.original_language"
        :voteAverage="TVShow.vote_average"
        :posterPath="TVShow.poster_path"/>
    </article>

  </main>
</template>

<style lang="scss" scoped>
  img{
    width: 30px;
  }
</style>