<script>

import { store } from "../store";

export default {
  data(){
    return{
      store,
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
    <div v-for="film in store.filmsList">{{film.title}}, {{film.original_title}}, <img :src="getImgPath(film.original_language)" :alt="film.original_language">, {{film.vote_average}}</div>
  </main>
</template>

<style lang="scss">
  img{
    width: 30px;
  }
</style>