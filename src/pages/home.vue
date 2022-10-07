<template>
  <div class="Home">
    <restaurentRow v-for="(data, i) in data_restaurant" :key="i" :restaurant_Info = "data"/>
  </div>
</template>

<script>
  //database imporation

  import BDD from '../BDD.js'

  import { onMounted, ref } from 'vue';

   //components
  import restaurentRow from '../components/RowComponent.vue'
export default {
    name:"HomePage",
    components:{
      restaurentRow,
    },
    setup(){
      // creating restaurant class where i'll stock my datas
      class Restaurant{
        constructor (name, note, image, drive_time){
          this.name = name;
          this.note = note;
          this.image = image;
          this.drive_time = drive_time;
        }
      }

      let data_restaurant = ref([]);

      const makeDataRestaurant = () =>{
        let restaurant__container = [];


        //iteration sur la base de donnees 
        for(const restaurant of BDD){
          const new_restaurant = new Restaurant(restaurant.name, restaurant.note, restaurant.image, restaurant.drive_time);
          
          if (restaurant__container.length === 2) {

            restaurant__container.push(new_restaurant);

            data_restaurant.value.push(restaurant__container);
            restaurant__container = [];
          }else{
            restaurant__container.push(new_restaurant);
          } 
        }

      }

     onMounted( makeDataRestaurant);

     return{
      data_restaurant,
     }
    }
}
</script>

<style>

</style>