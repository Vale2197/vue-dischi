<template>
  <div id="app">
    <siteHeader/>
   <!--  <siteMain/> -->
    <!-- <siteFooter/> -->
  </div>
</template>

<script>
import siteHeader from "./components/siteHeader.vue"

export default {
  name: 'App',
  components: {
    siteHeader
  }
}
</script>

<style lang="scss">
@import "../node_modules/bootstrap";
@import "./assets/variabili.scss";

</style>
