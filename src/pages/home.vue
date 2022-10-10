<template>
  <div class="Home">
    <header class="header">
      <img src="../components/img/imgcard.png" alt="logo">
      <form action="">
        <input type="text" name="search" id="search" placeholder="ou voulez-vous manger ?">
      </form>
    </header>
    <section>
      <div class="banner">

      </div>
      <restaurentRow v-for="(data, i) in data_restaurant" :key="i" :restaurant_Info = "data"/>
    </section>
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

<style lang="scss">

.Home{
  .header{
    width: 100%;
    height: 120px;
    background: #fff;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: fixed;
    z-index: 1;

    img{
      width: 200px;
      height: 90%;
      object-fit: cover;
    padding: 0 20px;
    }

    form{
      input{
        background-color: #f6f6f6;
        outline: none;
        border: none;
        height: 60px;
        width: 400px;
        padding: 10px;
        font-size: 20px;
      }
    }
  }

  section{
    width: 100%;
    height: auto;
    padding: 20px 0;
    position: relative;
    top: 5rem;
    display: flex;
    justify-content: center;
    align-content: center;
    flex-wrap: wrap;

    .banner{
      width: 100%;
      height: 200px;
      background-image: url("../components/img/imgcard.png");
      background-size: cover;
      background-position: center center;
    }
  }
}
</style>