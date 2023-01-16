<script>
export default {
  name: "FilmApp",
  props: [
    "film", 
    "flagsAvailable"
  ],
  data(){
    return{

    }
  },
  methods: {
    getImgPath(imgPath){
      return new URL(`../../assets/img/${imgPath}.png`, import.meta.url).href;
    }
  },

}
</script>

<template>
  <div>

    <span>{{ film.title }}, </span>
    <span>{{ film.original_title }}, </span>
    <img :src="flagsAvailable.includes(film.original_language) ? getImgPath(film.original_language) : getImgPath(`rainbow`)" :alt="film.original_language">
    <span>{{ film.vote_average }}</span>
    
  </div>
</template>

<style lang="scss">
  
</style>