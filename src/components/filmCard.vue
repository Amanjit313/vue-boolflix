<template>
  
  <div>
    <h1>Titolo Film: {{film.title}}</h1>
    <p>Titolo Originale: {{film.original_title}}</p>
    <p>Lingua: {{film.original_language}}</p>
    <p>Voto: {{film.vote_average}}</p>
    <hr>
  </div>

</template>

<script>
export default {
  name: "myMain",
  props: {
    film : Object
  }

}
</script>

<style lang="scss" scoped>

</style>