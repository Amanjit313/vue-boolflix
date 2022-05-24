<template>

  <div class="search-bar-container">

    <div class="logo">
      <h1>BOOLFLIX</h1>
    </div>

    <div class="search-bar">
      <div class="costum-border">
        <input v-model.trim = "movieToSearch" placeholder="Cerca un film" type="text" @keyup.enter="$emit('startSearch', movieToSearch, selector)">
        <button type="button" @click ="$emit('startSearch', movieToSearch, selector)">SEARCH</button>
      </div>

        <select v-model ="selector" @change ="$emit('startSearch', movieToSearch, selector)">
          <option value="film">Film</option>
          <option value="serie tv">Serie TV</option>
        </select>
    </div>

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

.search-bar-container{
  display: flex;
  padding: 20px;
  justify-content: space-between;
  border-bottom: 1px solid #E0E0E0;
}

h1{
  color: red;
}

.search-bar{
  display: flex;
  align-items: center;
}

.costum-border{
  padding: 10px;
  border: 1px solid #E0E0E0;
  border-radius: 5px;
}

input{
  margin-right: 5px;
  height: 2rem;
  border: none;
  background-color: transparent;
  border-bottom: 1px solid #E0E0E0;
  color: rgb(255, 255, 255);

  &:focus {
    outline: none;
    border-bottom: 1px solid #2196F3;
  }
}

button{
  padding: 10px;
  border-radius: 5px;
  background-color: #2196F3;
  color: white;
  border: #2196F3;

  &:hover{
    background-color: #0987ef;
  }
}

select{
  margin-left: 30px;
  padding: 10px;
  background-color: transparent;
  color: lightgray;
  border: #2196F3;
  border-left: 1px solid #E0E0E0;
  text-transform: uppercase;

  &:hover{
    color: white;
  }
}

</style>