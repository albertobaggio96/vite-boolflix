<script>
  export default {
    props:[
      "id",
      "apiKey"
    ],

    data(){
      return{
        creditsURL: "https://api.themoviedb.org/3/movie/",
      }
    }
  }

</script>

<template >
  <div>
    {{ apiKey }}
  </div>
</template>

<style lang="">
  
</style>