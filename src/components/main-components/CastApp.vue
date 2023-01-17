<script>
import axios from 'axios';


export default {
  props: [
    "id",
    "apiKey"
  ],

  data() {
    return {
      creditsURL: "https://api.themoviedb.org/3/movie/",
      castList : [],
    }
  },
  methods: {
    getCreditsURLMovie(){
      return `${this.creditsURL}${this.id}/credits`
    },
    getCastInfo() {
      axios.get(this.getCreditsURLMovie(), {
        params: {
          api_key: this.apiKey
        }
      })
        .then((response) =>{
          // console.log(response.data.cast);
          this.castList = response.data.cast
          console.log(this.castList)
        })
        .catch(function (error) {
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    }
  },
  created(){
    this.getCastInfo()
    this.getCastInfo()
  }
}

</script>

<template >
  <div v-for="cast in castList">
    {{ cast.name }}
  </div>
</template>

<style lang="">
  
</style>