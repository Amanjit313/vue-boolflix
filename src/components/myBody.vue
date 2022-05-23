<template>

  <div class="filmSearcher">

        <searchBar @startSearch="textToSearch" @selectorType="getAPI"/>

        <filmCard 
        v-for = "film in filmSearched" 
        :key="film.id"
        :film="film"
        />

  </div>

</template>

<script>
import axios from "axios"
import filmCard from "./filmCard.vue"
import searchBar from "./searchBar.vue"

export default {
  name: "myHeader",
  components: {
    filmCard,
    searchBar
  },

  data(){
    return{
      apiURLMovie: "https://api.themoviedb.org/3/search/movie",
      apiURLTv: "https://api.themoviedb.org/3/search/tv",
      apiParams: {
        api_key: "33253eee85c97808d758bc69d5359747",
        language: "it-IT",
        query: ""
      },
      filmSearched: []
    }
  },

  methods:{
    getAPI(whatToSee){
      console.log(whatToSee)
      if(whatToSee === "serie tv"){
        axios.get(this.apiURLTv, {
          params: this.apiParams
        })
        .then(res =>{
          console.log(res.data.results)
          this.filmSearched = res.data.results
          console.log(this.filmSearched)
        })
      } else{
          axios.get(this.apiURLMovie, {
          params: this.apiParams
        })
        .then(res =>{
          console.log(res.data.results)
          this.filmSearched = res.data.results
          console.log(this.filmSearched)
        })
      }
    },

    textToSearch(searcher){
      this.apiParams.query = searcher
      this.getAPI()
    },
  }
}
</script>

<style lang="scss" scoped>

.filmSearcher{
  display: flex;
  flex-direction: column;
}

</style>