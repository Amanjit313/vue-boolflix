<template>
  <div id="app">
    <myHeader />
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'

export default {
  name: 'App',
  components: {
    myHeader
  }
}
</script>

<style lang="scss">
@import "./assets/style/global";
@import "./assets/style/utils";

</style>
