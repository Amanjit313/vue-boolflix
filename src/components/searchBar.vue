<template>
  <div class="search-bar">
      <input v-model.trim = "movieToSearch" placeholder="Cerca un film" type="text" @keyup.enter="$emit('startSearch', movieToSearch)">
      <button type="button" @click ="$emit('startSearch', movieToSearch)">SEARCH</button>

      <select v-model ="selector" @change ="$emit('selectorType', selector)">
        <option value="film">Film</option>
        <option value="serie tv">Serie TV</option>
      </select>
  </div>
</template>

<script>
export default {
  name: "searchBar",

  data(){
    return{
      movieToSearch: "",
      selector: "film"
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

select{
  margin-left: 10px;
}

</style>