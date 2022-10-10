<template>
  <div class="restaurentRow">
    <h2 class="title">Nos restaurants</h2>
    <div class="cards__container">
        <restaurantCard v-for="(card, index) in restaurant_Info" :info_restaurantValue="card" :key="index"/>
    </div>
  </div>
</template>

<script>
    import restaurantCard from "./CardsComponent.vue"
export default {
    name: "restaurentRow",
    components: {
        restaurantCard,
    },
    props:{
        restaurant_Info: Array
    }
}
</script>

<style lang="scss">
    .restaurentRow{
        width: 90%;
        height: 50vh;
        .title{
            text-align: start;
            font-size: 30px;
            font-weight: bold;
        }
        .cards__container{
            width: 100%;
            height: 90%;
            display: flex;
            justify-content: space-around;
            align-items: center;
        }
    }

</style>