<script>
// impor component
import PosterApp from './PosterApp.vue';
import CastApp from "./CastApp.vue"

export default {
  name: "FilmApp",

  components:{
    PosterApp,
    CastApp,
  },

  props: [
  "title",
  "originalTitle",
  "originalLanguage",
  "originalLanguageFlag",
  "voteAverage",
  "posterPath",
  "id",
  "apiKey"
  ],
}
</script>

<template>

  <figure id="poster">
    <PosterApp :posterPath="posterPath" :title="title"/>
  </figure>
  

  <article id="info" class="p-2">
    <h1 class="w-100 fs-3">{{ title }}, </h1>
    <div>{{ originalTitle }}, </div>
    <figure class="mb-0">
      <img :src="originalLanguageFlag" :alt="originalLanguage">
    </figure>
    <div>
      <font-awesome-icon icon="fa-solid fa-star" v-for="star in voteAverage"/>
      <font-awesome-icon icon="fa-regular fa-star"  v-for="star in 5 - voteAverage"/>
    </div>
    <CastApp 
      :id="id"
      :apiKey="apiKey"/>
  </article>

</template>

<style lang="scss" scoped>
  figure#poster{
    width: 342px;
    height: 513px;
  }

  img{
    width: 30px;
  }
</style>