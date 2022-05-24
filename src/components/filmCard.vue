<template>
  
  <div class="cards-container w-80">

    <img class="empty-img" v-if="(film.poster_path === null)" :src="`	https://www.cobatyitalia.it/wp-content/uploads/2020/12/img-not-found.jpg`" alt="empty">
    <img v-else :src="`https://image.tmdb.org/t/p/w200/${film.poster_path}`" alt="poster">

    <div class="cards-text">
      <h1 class="cards-title">{{film.title || film.name}}</h1>

      <div class="p-overlay">
        <p class="cards-date">{{film.original_title || film.original_name}} | {{film.release_date}}</p>

        <p class="cards-without-flag" v-if="noFlag.includes(film.original_language)">Lingua: {{film.original_language}}</p>
        <p class="cards-flag" v-else><lang-flag :iso="film.original_language" :squared="false"/></p>

        <p class="cards-desc">{{film.overview}}</p>
      </div>

      <star-rating class="cards-vote" :star-size="25" :rating="film.vote_average/2" :read-only="true" :increment="0.1"></star-rating> 
    </div>

  </div>

</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import StarRating from 'vue-star-rating';

export default {
  name: "myMain",
  components: {
    LangFlag,
    StarRating
  },

  data(){
    return{
      noFlag : ["ml", "pa"]
    }
  },

  props: {
    film : Object
  }

}
</script>

<style lang="scss" scoped>

.cards-container{
  display: flex;
  border: 1px solid #E0E0E0;
  margin-top: 50px;
  position: relative;
}

.empty-img{
  width: 200px;
}

.cards-text{
  color: white;
  margin-left: 25px;
  flex-direction: column;
  display: flex;
}

.cards-title{
  margin-top: 1%;
}

.cards-date{
  margin-top: 1.5%;
  text-transform: uppercase;
  font-size: .95rem;
}

.cards-without-flag{
  margin-top: 1%;
  text-transform: uppercase;
  font-size: .7rem;
}

.cards-flag{
  margin-top: 1%;
}

.cards-desc{
  margin-right: 10px;
  height: 100px;
  overflow: auto;
  font-size: .85rem;
  margin-top: 1.5%;
  color: rgba($color: white, $alpha: .65);
}

.cards-vote{
  bottom: 0;
  position: absolute;
  margin-bottom: 1%;
}

</style>