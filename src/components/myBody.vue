<template>

  <div class="filmSearcher">

        <searchBar @startSearch="textToSearch"/>

        <div class="no-result-and-loading-from-search" v-if="this.filmSearched.length === 0">
          <h1>{{testoLoadingUno}}</h1>
          <p>{{testoLoadingDue}}</p>
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
      filmSearched: [],
      testoLoadingUno: "Cerca un Film o una serie TV!",
      testoLoadingDue: "In alto a destra trovi la search dove cercare!"
    }
  },

  methods:{
    getAPI(whatToSee){
      console.log(whatToSee);
      if(whatToSee === "serie tv"){
        axios.get(this.apiURLTv, {
          params: this.apiParams
        })
        .then(res =>{
          console.log(res.data.results);
          this.filmSearched = res.data.results;
          if (this.filmSearched.length === 0){
            this.testoLoadingUno = "Nessun risultato";
            this.testoLoadingDue = "Riprova a cercare!";
          }
          console.log(this.filmSearched);
        })
      } else{
        axios.get(this.apiURLMovie, {
          params: this.apiParams
        })
        .then(res =>{
          console.log(res.data.results);
          this.filmSearched = res.data.results;
          if (this.filmSearched.length === 0){
            this.testoLoadingUno = "Nessun risultato";
            this.testoLoadingDue = "Riprova a cercare!";
          }
          console.log(this.filmSearched);
        })
      }
    },

    textToSearch(searcher, type){
      this.apiParams.query = searcher;
      this.testoLoadingUno = "Sta caricando";
      this.testoLoadingDue= "Attendere qualche secondo!";
      this.filmSearched = [];
      this.getAPI(type);
    },
  }
}
</script>

<style lang="scss" scoped>

.filmSearcher{
  display: flex;
  flex-direction: column;
}

.no-result-and-loading-from-search{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgba($color: black, $alpha: .5);
  padding: 50px;
  margin-top: 25vh;
  text-transform: uppercase;
}

h1{
  color: red;
  background-color: transparent;
  border-bottom: 1px solid #E0E0E0;
  padding: 10px;
  width: 30%;
  text-align: center;
}

p{
  background-color: transparent;
  color: darkgray;
  margin-top: 10px;
}

</style>