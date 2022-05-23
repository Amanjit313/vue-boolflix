<template>
  <div class="search-bar">
      <input v-model.trim = "movieToSearch" placeholder="Cerca un film" type="text" @keyup.enter="$emit('startSearch', movieToSearch)">
      <button type="button" @click ="$emit('startSearch', movieToSearch)">SEARCH</button>
  </div>
</template>

<script>
export default {
  name: "searchBar",

  data(){
    return{
      movieToSearch: ""
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