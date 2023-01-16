<script>
export default {
  name: "TVShowApp",
  props: [
    "TVShow", 
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

    <span>{{ TVShow.name }}, </span>
    <span>{{ TVShow.original_name }}, </span>
    <img :src="flagsAvailable.includes(TVShow.original_language) ? getImgPath(TVShow.original_language) : getImgPath(`rainbow`)" :alt="TVShow.original_language">
    <span>{{ TVShow.vote_average }}</span>

  </div>
</template>

<style lang="scss">
  
</style>