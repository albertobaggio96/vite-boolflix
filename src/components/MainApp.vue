<script>

import { store } from "../store";

export default {
  data(){
    return{
      store,
      flagsAvailable: ["de", "en", "es", "fi", "fr", "it", "ja", "ko", "pl", "zh"]
    }
  },
  methods:{
    getImgPath(imgPath){
      return new URL(`../assets/img/${imgPath}.png`, import.meta.url).href;
    }
  },
}
</script>

<template>
  <main>
    <h1>Film</h1>
    <div v-for="film in store.filmsList">
      {{film.title}}, {{film.original_title}}, <img v-if="flagsAvailable.includes(film.original_language)" :src="getImgPath(film.original_language)" :alt="film.original_language"> <img v-else src="../assets/img/rainbow.png" :alt="film.original_language">, {{film.vote_average}}
    </div>
    <h1>TV series</h1>
  </main>
</template>

<style lang="scss">
  img{
    width: 30px;
  }
</style>