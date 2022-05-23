<template>
  
  <div>
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

</style>