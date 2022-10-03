<template>
  <div id="app">
    <restaurant-card/>
  </div>
</template>

<script>

import restaurantCard from './components/CardsComponent.vue'

export default {
  name: 'App',
  components: {
    restaurantCard
  }
}
</script>

<style>
  @import url('./css/reset.css');
  @import url("https://fonts.googleapis.com/css2?family=Roboto%3Awght%40300%3B400%3B700&display=swap");
#app {
  font-family: "Roboto", sans-serif;
}
</style>
