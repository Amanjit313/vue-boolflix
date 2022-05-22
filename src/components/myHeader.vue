<template>

  <div class="filmSearcher">
      <div class="search-bar">
        <input v-model.trim = "apiParams.query" placeholder="Cerca un film" type="text" @keyup.enter="getAPI()">
        <button type="button" @click = "getAPI()">SEARCH</button>
      </div>

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

export default {
  name: "myHeader",
  components: {
    filmCard
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

  mounted(){
    this.getAPI()
  },

  methods:{
    getAPI(){
      axios.get(this.apiURL, {
        params: this.apiParams
      })
      .then(res =>{
        console.log(res.data.results)
        this.apiParams.query = ""
        this.filmSearched = res.data.results
        console.log(this.filmSearched)
      })
    }
  }
}
</script>

<style lang="scss" scoped>

.filmSearcher{
  display: flex;
  flex-direction: column;
}

.search-bar{
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

input{
  margin-right: 20px;
  height: 2rem;
}

button{
  padding: 5px;
  border-radius: 5px;
}

</style>