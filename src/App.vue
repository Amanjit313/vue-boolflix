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
- Sistemare gli elementi che non hanno una immagine di default dandone una dinamicamente
