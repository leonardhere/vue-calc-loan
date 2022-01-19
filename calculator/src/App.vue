<template>
  <div id="app">
    <div class="calculator__head">
      <h2 class="calculator__head-title">«Краткосрочный займ» в Таганроге</h2>
      <inputs/>
    </div>
    <calc-body/>
  </div>
</template>

<script>
import Inputs from './components/inputs.vue'
import CalcBody from './components/calcbody.vue'
export default {
  name: 'App',
  components: {
    Inputs,
    CalcBody
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 5%;
  background: #2ba1d4;
}

.calculator__head h2{
  text-align: center;
}

.calculator__head{
  padding: 30px 67px;
  background-color: #fcfeff;
  box-shadow: 0 0 40px 0 rgb(0 0 0 / 10%);
  border-top-right-radius: 20px;
  border-top-left-radius: 20px;
}
</style>
