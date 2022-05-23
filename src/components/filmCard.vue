<template>
  
  <div>
    <img :src="`https://image.tmdb.org/t/p/w300/${film.poster_path}`" alt="">
    <h1>{{film.title || film.name}}</h1>
    <p>{{film.original_title || film.original_name}}</p>
    <p><lang-flag :iso="film.original_language" :squared="false"/></p>
    <star-rating :rating="film.vote_average/2" :read-only="true" :increment="0.1"></star-rating>
    <hr>
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
  props: {
    film : Object
  }

}
</script>

<style lang="scss" scoped>

div h1,
div p,
div img{
  margin-left: 10px;
}

</style>