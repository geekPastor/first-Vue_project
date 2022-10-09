<template>
  <div class="restaurantCard">
    <div :style="changebackgroundImage" class="cardimage">

    </div>
    <div class="cardinfo">
      <div class="top">
        <p class="name">{{info_restaurantValue.name}}</p>
        <p class="note">
          <span>{{info_restaurantValue.note}}</span>
        </p>
      </div>
      <p class="time">{{info_restaurantValue.drive_time}}</p>
    </div>
  </div>
</template>

<script>

import {computed} from 'vue'
//import { onMounted } from '@vue/runtime-core'
export default {
  name: "CardsComponent",
  props:{
    info_restaurantValue: Object,
  },
  setup(props){
    const changebackgroundImage = computed(()=>{
      return{
        backgroundImage: `url(${props.info_restaurantValue.image})`
      }
    });
 
    return{
      changebackgroundImage
    }
  }
}
</script>

<style lang="scss">
.restaurantCard{
    width: 32%;
    height: 30vh;
   
   
    p{
      margin: 0px;
    }

    .cardimage{
      background-image: url('img/imgcard.png'); 
      background-size: cover;
      background-position: center;
      height: 70%;
      width: 100%;
    }

    .cardinfo{
     
      .top{
        margin: 10px 0px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        .note{
          background: #eeeeee;
          height: 30px;
          width: 30px;
          display: flex;
          justify-content: center;
          align-items: center;
          font-size: 0.9rem;
          border-radius: 50%;
        }
      }

      .time{
        font-size: 0.9rem;
      }
    }
}
</style>