<template>
  <div id="app">
    <siteHeader/>
    <siteMain/>
    <!-- <siteFooter/> -->
  </div>
</template>

<script>
import siteHeader from "./components/siteHeader.vue"
import siteMain from "./components/siteMain.vue"

export default {
  name: 'App',
  components: {
    siteHeader,
    siteMain
  }
}
</script>

<style lang="scss">
@import "../node_modules/bootstrap";
@import "./assets/variabili.scss";

body {
  background-color: $bg_body;
}

</style>
