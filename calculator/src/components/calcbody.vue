<template>
<div class="calc-main">
    <table class="left__blok">
    <tr class="left-block-row">
      <div class="left-block-row-up">
        <td>Вы занимаете</td>
        <td>
          <input v-model.number="price" class="input calc__input">
        </td>
      </div>
      <td colspan="2" class="left-block-range">
        <input class="input--range" type="range" min="5000" max="100000" step="1000" v-model="price">
      </td>
    </tr>
    <tr>
    </tr>
    <tr class="left-block-row">
      <div class="left-block-row-up">
        <td>На срок</td>
        <td>
          <input v-model.number="term" class="input calc__input">
        </td>
      </div>
      <td colspan="2" class="left-block-range">
        <input class="input--range" type="range" min="1" max="25" step="1" v-model="term">
      </td>
    </tr>
    <tr>
    </tr>
  </table>
  <table class="right__block">
    <tr v-for="program in programs" :key="program.id" class="right_column">
      <td>Процентная ставка <br> {{year_rate(program)}}%</td>
      <td class="ra">Сумма к возврату <br> {{ tax(program) }} $</td>
    </tr>
    <a href="#" class="solution">Получить решение по займу</a>
  </table>
</div>
</template>

<script>
export default{
  data() {
    return{
      price: 60000,
      initial_fee: 3000,
      term: 5,
      programs: [{
        title: 'Tinkoff',
        rate: 0.045,
      }]
    }
  },
  methods: {
    year_rate: function(program) {
      return (program.rate * 100).toFixed(1);
    },
    tax: function(program) {
      var i = program.rate / 12;
      var n = this.term * 12;
      var x = Math.pow(1 + i, n)
      var sum = this.price - this.initial_fee;
      return Math.round(sum * (i * x) / (x - 1));
    },
  },
  watch: {
    price: function(value) {
      this.price < this.initial_fee && (this.initial_fee = this.price);
    },
    initial_fee: function(fee) {
      this.initial_fee > this.price && (this.initial_fee = this.price);
    },
  }

}
</script>


<style scoped>
.left__blok{
  width: 70%;
}

.left-block-row-up{
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.left-block-row-up td input{
  border-radius: 6px;
  background: #ffffff;
  border: solid 1px #e9eeee;
  padding: 9px 13px;
  color: #21405b;
}

.left-block-range{
  display: flex;
}

.ra {
  text-align: center;
}

input {
  width: 100%;
}

.calc-main{
  display: flex;
  padding: 30px 67px 50px;
  background-color: #fcfeff;
  box-shadow: 0 0 40px 0 rgb(0 0 0 / 10%);
  border-bottom-right-radius: 20px;
  border-bottom-left-radius: 20px;
  justify-content: space-between;
}
.right__block{
}
.right_column{
  display: flex;
  flex-direction: column;
  align-items: center;
  background: linear-gradient(250deg, #2ba1d4 0%,#2b57d4 100%);
  text-align: center;
  color: #ffffff;
  padding: 29px 0;
  border-radius: 14px;
  margin-bottom: 20px;
}

.solution{
    width: 100%;
    height: 50px;
    line-height: 50px;
    font-size: 16px;
    font-weight: 300;
    color: #ffffff;
    background: #ff4533;
    padding: 15px 20px;
    text-decoration: none;
    border-radius: 100px;
}

.calc__input{
  width: 81%;
}
</style>