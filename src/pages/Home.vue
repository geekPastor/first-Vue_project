<template>
  <div class="HomePage">
    <restaurentRow />
  </div>
</template>

<script>
  import restaurentRow from '../components/RowComponent.vue'
export default {
    name:"Home",
    components:{
      restaurentRow,
    }
}
</script>

<style>

</style>