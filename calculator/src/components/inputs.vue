<template>
  <div class="select-group">
    <inputs-item-obl/>
    <inputs-item-city/>
    <inputs-item-otd/>
    <inputs-items-stat/>
  </div>
</template>

<script>
import InputsItemObl from './inputitem-obl.vue'
import InputsItemCity from './inputsitem-city.vue'
import InputsItemOtd from './inputsitem-otdel.vue'
import InputsItemsStat from './inputsitem-stat.vue'
export default {
  name: 'App',
  components: {
      InputsItemObl,
      InputsItemCity,
      InputsItemOtd,
      InputsItemsStat
  }
}
</script>


<style scoped>
  .select-group{
    display: flex;
    justify-content: space-evenly;
  }
  @media (max-width: 768px){
    .select-group{
      flex-wrap: wrap;
    }
  }
</style>