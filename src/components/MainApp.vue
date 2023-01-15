<script>

import { store } from "../store";

export default {
  data(){
    return{
      store,
    }
  }
  
}
</script>

<template>
  <main>
    <div v-for="film in store.filmsList">{{film.title}}, {{film.original_title}}, {{film.original_language}}, {{film.vote_average}}</div>
  </main>
</template>

<style lang="scss">
  
</style>