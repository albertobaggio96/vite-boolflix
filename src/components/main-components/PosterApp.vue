<script>
export default {
  name: "PosteApp",

  props:[
    "posterPath",
    "title"
  ],

  data(){
    return{
      imgURL: "https://image.tmdb.org/t/p/",
      imgWidth: "w342",
    }
  },
  methods:{
    getPoster(){
      if (this.posterPath !== null){
        return `${this.imgURL}${this.imgWidth}${this.posterPath}`
      }
      else{
      return new URL(`../../assets/img/n.png`, import.meta.url).href;
      }
    }
  }
}
</script>

<template>
  <div>
    <img :src="getPoster()" :alt="title">
  </div>
</template>

<style lang="scss" scoped>
  img{
    width: 342px;
    height: 513px;
    object-fit: cover;
    object-position: top;
  }
</style>