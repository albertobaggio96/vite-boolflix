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

  <PosterApp :posterPath="posterPath" :title="title"/>

  <span>{{ title }}, </span>
  <span>{{ originalTitle }}, </span>
  <img :src="originalLanguageFlag" :alt="originalLanguage">
  <font-awesome-icon icon="fa-solid fa-star" v-for="star in voteAverage"/>
  <font-awesome-icon icon="fa-regular fa-star"  v-for="star in 5 - voteAverage"/>

</template>

<style lang="scss" scoped>
  img{
    width: 30px;
  }
</style>