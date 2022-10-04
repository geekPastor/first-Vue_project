<template>
  <div class="restaurentRow">
    <h2 class="title">Nos restaurants</h2>
    <restaurantCard v-for="(card, index) in 3" :key="index"/>
  </div>
</template>

<script>
    import restaurantCard from "./CardsComponent.vue"
export default {
    name: "RowComponent",
    components: {
        restaurantCard,
    }
}
</script>

<style>

</style>