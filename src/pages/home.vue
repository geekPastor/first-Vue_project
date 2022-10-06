<template>
  <div class="Home">
    <restaurentRow />
  </div>
</template>

<script>
  //database

  import BDD from '../BDD.js'

   //components
  import restaurentRow from '../components/RowComponent.vue'
export default {
    name:"HomePage",
    components:{
      restaurentRow,
    },
    setup(){
      class Restaurant{
        constructor (name, note, image, drive_time){
          this.name = name;
          this.note = note;
          this.image = image;
          this.drive_time = drive_time;
        }
      }

      var resto = new Restaurant('toto')
      console.log(BDD);
      console.log(resto);
    }
}
</script>

<style>

</style>