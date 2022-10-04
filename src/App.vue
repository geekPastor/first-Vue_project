<template>
  <div id="app">
    <HomePage />
  </div>
</template>

<script>


import HomePage from "./pages/homePage.vue"

export default {
  name: 'App',
  components:{
    HomePage,
  }
}
</script>

<style>
  @import url('./css/reset.css');
  @import url("https://fonts.googleapis.com/css2?family=Roboto%3Awght%40300%3B400%3B700&display=swap");
#app {
  font-family: "Roboto", sans-serif;
  padding: 20px;
}
</style>
