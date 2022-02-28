<template>
<div class="calc-main">
    <div class="left__blok">
    <div class="left-block-row">
      <div class="left-block-row-inside">
          <div class="left-block-row-up">
          <div>Вы занимаете</div>
          <div class="input_container">
            <input v-model.number="price" class="input calc__input">
          </div>
          </div>
          <div class="left-block-sum">
            <div class="sum-min">1 000</div>
            <div class="sum-max">30 000</div>
        </div>
      </div>
      <div class="left-block-range">
        <input class="input--range" type="range" min="5000" max="30000" step="1000" v-model="price">
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
        <div class="left-block-sum">
            <div class="sum-min">1</div>
            <div class="sum-max">60</div>
        </div>
      </div>
      <div class="left-block-range">
        <input class="input--range" type="range" min="1" max="60" step="1" v-model="term">
      </div>
    </div>
  </div>
  <div class="right__block">
    <div v-for="program in programs" :key="program.id" class="right_column">
      <div>Процентная ставка <br> {{year_rate(program)}}%</div>
      <div class="ra">Сумма к возврату <br> <span> {{ tax(program) }} ₽</span></div>
    </div>
    <a href="#" class="solution">Получить решение по займу</a>
  </div>
</div>
</template>

<script>
export default{
  data() {
    return{
      price: 15000,
      initial_fee: 1,
      term: 15,
      programs: [{
        rate: 0.01,
      }]
    }
  },
  methods: {
    year_rate: function(program) {
      return (program.rate * 100).toFixed(1);
    },
    tax: function(program) {
      const i = program.rate / 365;
      const n = this.term / 12;
      const x = Math.pow(1 + i, n)
      const sum = this.price + this.initial_fee;
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

.left-block-sum{
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