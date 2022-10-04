<template>
  <div id="app">
    <restaurentRow v-for="(cards, index) in 3" :key="index"/>
  </div>
</template>

<script>

import restaurentRow from './components/RowComponent.vue';

export default {
  name: 'App',
  components: {
    restaurentRow,
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
