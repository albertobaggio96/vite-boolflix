<script>
// impor component
import PosterApp from './PosterApp.vue';

export default {
  name: "FilmApp",

  components:{
    PosterApp
  },

  props: [
  "title",
  "originalTitle",
  "originalLanguage",
  "originalLanguageFlag",
  "voteAverage",
  "posterPath"
  ],
}
</script>

<template>

  <div id="poster">
    <PosterApp :posterPath="posterPath" :title="title"/>
  </div>

  <div id="film-info">
    <span>{{ title }}, </span>
    <span>{{ originalTitle }}, </span>
    <img :src="originalLanguageFlag" :alt="originalLanguage">
    <font-awesome-icon icon="fa-solid fa-star" v-for="star in voteAverage"/>
    <font-awesome-icon icon="fa-regular fa-star"  v-for="star in 5 - voteAverage"/>
  </div>

</template>

<style lang="scss" scoped>
  img{
    width: 30px;
  }
</style>