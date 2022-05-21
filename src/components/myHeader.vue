<template>
  <h1>myHeader</h1>
</template>

<script>
import axios from "axios"

export default {
  name: "myHeader",

  data(){
    return{
      apiURL: "https://api.themoviedb.org/3/search/movie",
      apiParams: {
        api_key: "33253eee85c97808d758bc69d5359747",
        language: "it-IT",
        query: "abcd"
      }
    }
  },

  mounted(){
    this.getAPI()
  },

  methods:{
    getAPI(){
      axios.get(this.apiURL, {
        params: this.apiParams
      })
      .then(res =>{
        console.log(res.data)
      })
    }
  }
}
</script>

<style lang="scss" scoped>

</style>