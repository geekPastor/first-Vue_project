<template>
  <div class="Home">
    <header class="header">
      <img src="../components/img/imgcard.png" alt="logo">
      <form action="">
        <input type="text" name="search" id="search" placeholder="ou voulez-vous manger ?" v-model="user_search_restaurant">

        <div class="search_hint">
           <div v-for="(restaurant, i) in search_restaurant" :key="i" class="container__search">
            <div class="wrapper__image">
              <img :src="restaurant.image" alt="">
            </div>
            <h2>{{restaurant.name}}</h2>
           </div>
        </div>
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

  import { onMounted, ref, watch } from 'vue';

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
      let all_restaurant = []

      const makeDataRestaurant = () =>{
        let restaurant__container = [];


        //iteration sur la base de donnees 
        for(const restaurant of BDD){
          const new_restaurant = new Restaurant(restaurant.name, restaurant.note, restaurant.image, restaurant.drive_time);
          all_restaurant.push(new_restaurant)
          if (restaurant__container.length === 2) {

            restaurant__container.push(new_restaurant);

            data_restaurant.value.push(restaurant__container);
            restaurant__container = [];
          }else{
            restaurant__container.push(new_restaurant);
          } 
        }

      }

      //user search restaurant
      let user_search_restaurant = ref('');
      let search_restaurant = ref([]);

      watch(user_search_restaurant, (new_value)=>{
        let regex = RegExp(new_value.toLowerCase());

        let new_search_restaurant = all_restaurant.filter(restaurant => regex.test(restaurant.name.toLowerCase()))
        search_restaurant.value = new_search_restaurant;
      })

     onMounted( makeDataRestaurant);

     return{
      data_restaurant,
      user_search_restaurant,
      search_restaurant
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
      margin-right: 30px;
      position: relative;
      input{
        background-color: #f6f6f6;
        outline: none;
        border: none;
        height: 60px;
        width: 400px;
        padding: 10px;
        font-size: 20px;
      }
      .search_hint{
        position: absolute;
        top: 100%;
        width: 100%;
        height: 400px;
        background-color: #fff;
        border: 1px solid #000;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        gap: 10px;
        overflow: scroll;

        .container__search{
          width: 70%;
          height: 50px;
          border: 1px solid #000;
          display: flex;
          justify-content: center;
          align-items: center;

          .wrapper__image{
            width: 10%;
            height: 90%;
            border: 1px solid #000;
            border-radius: 50%;

            img{
              width: 100%;
              height: 100%;
              border-radius: 50%;
              object-fit: cover;
            }
          }
        }
      }
    }
  }

  section{
    width: 100%;
    height: auto;
    padding: 20px 0;
    position: relative;
    top: 6rem;
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