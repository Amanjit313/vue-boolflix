<template>

  <div class="search-bar">
    <input v-model.trim = "apiParams.query" placeholder="Cerca un film" type="text" @keyup.enter="getAPI()">
    <button type="button" @click = "getAPI()">SEARCH</button>
  </div>

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
        query: ""
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
        this.apiParams.query = ""
      })
    }
  }
}
</script>

<style lang="scss" scoped>

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