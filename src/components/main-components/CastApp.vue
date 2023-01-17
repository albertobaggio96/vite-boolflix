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
      nameCastList:[],
      allCast : false
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
          response.data.cast.forEach(cast =>{
            this.nameCastList.push(cast.name)
          })

        })
        .catch(function (error) {
          console.log(error);
        })
        .then(function () {
          // always executed
        });
    },
  },
  created(){
    this.getCastInfo()
    this.getCastInfo()
    
  }
}

</script>

<template >
  <div v-if="nameCastList.length > 5 && !allCast">
    <p>{{ nameCastList.slice(0, 4).join(", ") }}...</p>
    <button class="btn btn-light" @click="allCast = !allCast">See all</button>
  </div>
  <div v-else @mouseleave="allCast = false">
    <p >{{ nameCastList.join(", ") }}</p>
    <button class="btn btn-light" v-if="nameCastList.length > 5" @click="allCast = !allCast">See less</button>
  </div>
</template>

<style lang="">
  
</style>