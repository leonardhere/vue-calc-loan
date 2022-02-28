<template>
    <div class="main-calc">
            <div class="calculator__head">
            <h2 class="calculator__head-title">«Краткосрочный займ» в Таганроге</h2>
            <inputs/>
        </div>
        <calcbody/>
    </div>
</template>

<script>
import Inputs from './inputs.vue'
import Calcbody from './calcbody.vue'
export default {
  name: 'MainCalc',
  components: {
    Inputs,
    Calcbody
  }
}
</script>

<style scoped>
    .main-calc{
        max-width: 1140px;
    }
</style>
