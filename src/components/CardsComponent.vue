<template>
  <div class="restaurantCard">
    <div class="cardimage">

    </div>
    <div class="cardinfo">
      <div class="top">
        <p class="name">{{info_restaurantValues.name}}</p>
        <p class="note">
          <span>{{info_restaurantValues.note}}</span>
        </p>
      </div>
      <p class="time">{{info_restaurantValues.drive_time}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardsComponent",
  props:{
    info_restaurantValue: Object
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