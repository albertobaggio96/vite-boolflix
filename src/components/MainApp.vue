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
  <main class="bg-dark p-4 text-white">

    <section class="mb-4">
      <h2>Film</h2>
      <div class="d-flex">
        <article v-for="film in store.filmsList">
          <ComponentFilmSeries  
            :title="film.title" 
            :originalTitle="film.original_title" 
            :originalLanguageFlag="getImgPath(film.original_language)"
            :originalLanguage="film.original_language"
            :voteAverage="getUntilFiveStar(film)"
            :posterPath="film.poster_path"/>
        </article>
      </div>
    </section>
    
    <section>
      <h2>TV show</h2>
      <div class="d-flex">
        <article v-for="TVShow in store.TVShowList">
          <ComponentFilmSeries 
            :title="TVShow.name" 
            :originalTitle="TVShow.original_name" 
            :originalLanguageFlag="getImgPath(TVShow.original_language)"
            :originalLanguage="TVShow.original_language"
            :voteAverage="getUntilFiveStar(TVShow)"
            :posterPath="TVShow.poster_path"/>\
        </article>
      </div>
    </section>

  </main>
</template>

<style lang="scss">

  main section{
    width: 100%;
    overflow-x: auto;
  }
  article{
    #info{
      display: none;
      width: 342px;
      height: 513px;
    }
    &:hover{
      #info{
        display: inline-block;
        
      }
      #poster{
        display: none
      }
    }
  }
</style>