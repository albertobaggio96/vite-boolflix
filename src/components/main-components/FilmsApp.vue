<script>
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

  <PosterApp :posterPath="posterPath"/>

  <span>{{ title }}, </span>
  <span>{{ originalTitle }}, </span>
  <img :src="originalLanguageFlag" :alt="originalLanguage">
  <span>{{ voteAverage }}</span>

</template>

<style lang="scss" scoped>
  img{
    width: 30px;
  }
</style>