<script>
export default {
  name: "PosteApp",

  props:["posterPath"],

  data(){
    return{
      imgURL: "https://image.tmdb.org/t/p/",
      imgWidth: "w342",
    }
  },
  methods:{
    getPoster(){
      return `${this.imgURL}${this.imgWidth}${this.posterPath}`
    }
  }
}
</script>

<template>
  <div>
    <img :src="getPoster()" alt="">
  </div>
</template>

<style lang="scss">
  
</style>