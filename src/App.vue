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
