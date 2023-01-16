<script>

// import store.js
import { store } from "../store.js";

// import components
import ComponentFilmSeries from "./main-components/ComponentFilmSeries.vue"

export default {
  name: "MainApp",

  components:{
    ComponentFilmSeries,
  },

  data(){
    return{
      store,
      flagsAvailable: ["de", "en", "es", "fi", "fr", "it", "ja", "ko", "pl", "zh"],
    }
  },
  methods:{
    getImgPath(imgPath){
      imgPath = this.flagsAvailable.includes(imgPath) ? imgPath : "rainbow";
      return new URL(`../assets/img/${imgPath}.png`, import.meta.url).href;
    },

    isFlagAvailable(imgPath){
      this.getImgPath (imgPath);
    },

    getUntilFiveStar(element){
      let fiveStar = Math.ceil(element.vote_average / 2)
      return fiveStar
    },
  },
}
</script>

<template>
  <main>

    <section class="d-flex">
      <article v-for="film in store.filmsList">
        <ComponentFilmSeries  
          :title="film.title" 
          :originalTitle="film.original_title" 
          :originalLanguageFlag="getImgPath(film.original_language)"
          :originalLanguage="film.original_language"
          :voteAverage="getUntilFiveStar(film)"
          :posterPath="film.poster_path"/>
      </article>
    </section>
    
    <section class="d-flex">
      <article v-for="TVShow in store.TVShowList">
        <ComponentFilmSeries 
          :title="TVShow.name" 
          :originalTitle="TVShow.original_name" 
          :originalLanguageFlag="getImgPath(TVShow.original_language)"
          :originalLanguage="TVShow.original_language"
          :voteAverage="getUntilFiveStar(TVShow)"
          :posterPath="TVShow.poster_path"/>\
      </article>
    </section>

  </main>
</template>

<style lang="scss" scoped>
  img{
    width: 30px;
  }
</style>