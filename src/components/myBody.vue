<template>

  <div class="filmSearcher">

        <searchBar @startSearch="textToSearch"/>

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
      apiURL: "https://api.themoviedb.org/3/search/movie",
      apiParams: {
        api_key: "33253eee85c97808d758bc69d5359747",
        language: "it-IT",
        query: ""
      },
      filmSearched: []
    }
  },

  methods:{
    getAPI(){
      axios.get(this.apiURL, {
        params: this.apiParams
      })
      .then(res =>{
        console.log(res.data.results)
        this.filmSearched = res.data.results
        console.log(this.filmSearched)
      })
    },

    textToSearch(searcher){
      this.apiParams.query = searcher
      this.getAPI()
    }
  }
}
</script>

<style lang="scss" scoped>

.filmSearcher{
  display: flex;
  flex-direction: column;
}

</style>