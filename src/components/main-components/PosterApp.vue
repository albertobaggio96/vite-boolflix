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
    <img :src="getPoster()" :alt="title" class="w-100 h-100">
</template>
