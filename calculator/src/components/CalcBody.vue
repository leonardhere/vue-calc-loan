<template>
<div class="calc-main">
    <div class="left__blok">
    <div class="left-block-row">
      <div class="left-block-row-inside">
          <div class="left-block-row-up">
          <div>Вы занимаете</div>
          <div class="input_container">
            <input v-model.number="amount" class="input calc__input">
          </div>
          </div>
          <div class="left-block-amount">
            <div class="amount-min">{{ amountMin }}</div>
            <div class="amount-max">{{ amountMax }}</div>
        </div>
      </div>
      <div class="left-block-range">
        <Range :min="amountMin" :max="amountMax" :step="amountStep" v-model="amount" />
      </div>
    </div>
    <div class="left-block-row">
      <div class="left-block-row-inside">
        <div class="left-block-row-up">
        <div>На срок</div>
        <div class="input_container">
          <input v-model.number="term" class="input calc__input">
        </div>
      </div>
        <div class="left-block-amount">
            <div class="amount-min">{{ termMin }}</div>
            <div class="amount-max">{{ termMax }}</div>
        </div>
      </div>
      <div class="left-block-range">
        <Range :min="termMin" :max="termMax" :step="termStep" v-model="term" />
      </div>
    </div>
  </div>
  <div class="right__block">
    <div class="right_column">
      <div>Процентная ставка <br> {{ initial_fee }}%</div>
      <div class="ra">Сумма к возврату <br> <span> {{ repayment() }} ₽</span></div>
    </div>
    <a href="#" class="solution">Получить решение по займу</a>
  </div>
</div>
</template>

<script>
import Range from './Inputs/Range'

export default {
  name: 'CalcBody',
  components: {
    Range
  },
  data() {
    return {
      amount: 15000,
      initial_fee: 1,
      term: 15,

      amountMin: 5000,
      amountMax: 30000,
      amountStep: 1000,

      termMin: 1,
      termMax: 60,
      termStep: 1,
    }
  },
  methods: {
    repayment() {
      return Math.round(this.amount + (((this.amount / 100) / this.initial_fee) * this.term));
    },
  },
}
</script>

<style scoped>
.ra {
    opacity: 0.8;
    font-size: 14px;
    font-weight: 500;
    letter-spacing: 0.3px;
    color: #fcfeff;
}

.ra span {
  opacity: 1;
  font-size: 38px;
}

.left__blok{
  width: 70%;
  margin-right: 20px;
}

.calc__input[data-v-4d4eba07]{
  border-radius: 6px;
  background: #ffffff;
  border: solid 1px #e9eeee;
  padding: 9px 13px;
  color: #21405b;
  width: 30%;
}

.input_container{
    display: flex;
    justify-content: right;
}

.left-block-amount{
  display: flex;
  justify-content: space-between;
}

.left-block-row-up{
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
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

input[type='range']::-webkit-slider-thumb{
  background: #ff4533;
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
  width: 280px;
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
  position: relative;
}

.right_column::before{
  position: absolute;
    top: 100%;
    left: 50%;
    content: '';
    margin-left: -8px;
    border-width: 8px 8px 0;
    border-style: solid;
    border-color: #2b77d4 transparent;
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

@media (max-width: 768px){
  .calc-main{
    display: flex;
    flex-direction: column;
  }
  .left__blok{
    width: 100%;
  }
  .right__block{
    width: 100%;
  }
}
@media (max-width: 425px){
    .calc-main{
      padding: 30px 20px 50px;
  }
}
</style>