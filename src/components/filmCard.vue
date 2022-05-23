<template>
  
  <div>
    <img :src="`https://image.tmdb.org/t/p/w300/${film.poster_path}`" alt="">
    <h1>Titolo Film: {{film.title || film.name}}</h1>
    <p>Titolo Originale: {{film.original_title || film.original_name}}</p>
    <p><lang-flag :iso="film.original_language" :squared="false"/></p>
    <p>Voto: {{film.vote_average}}</p>
    <hr>
  </div>

</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: "myMain",
  components: {
    LangFlag
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