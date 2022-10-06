<template>
  <div class="Home">
    <restaurentRow />
  </div>
</template>

<script>
  //database imporation

  import BDD from '../BDD.js'

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

      let data_restaurant = [];

      const makeDataRestaurant = () =>{
        let restaurant__container = [];

        
        //iteration sur la base de donnees
        for(const restaurant of BDD){
          const new_restaurant = new Restaurant(restaurant.name, restaurant.note, restaurant.image, restaurant.drive_time);
          restaurant__container.push(new_restaurant);
        }

      }

      makeDataRestaurant();
    }
}
</script>

<style>

</style>