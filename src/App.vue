<template>
  <div id="app">
    <myBody />
  </div>
</template>

<script>
import myBody from './components/myBody.vue'

export default {
  name: 'App',
  components: {
    myBody
  }
}
</script>

<style lang="scss">
@import "./assets/style/global";
@import "./assets/style/utils";

</style>

/* PROMEMORIA DEGLI ERRORI */
- Sistemare le bandiere non presenti nella cdn,
- Sistemare il bug se ho già cliccato serie tv e cerco qualcosa mi mostra comunque prima e film e dopo ricliccato film e serie tv mi mostra le serie tv prima no,
- Sistemare gli elementi che non hanno una immagine di default dandone una dinamicamente
