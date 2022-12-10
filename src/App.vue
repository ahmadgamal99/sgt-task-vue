<template>
  <div id="app">
    <landing-page-view></landing-page-view>
  </div>
</template>

<script>

import LandingPageView from "@/Views/LandingPageView";

export default {
  name: 'App',
  components: {
    LandingPageView
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #13263C;

}
</style>
