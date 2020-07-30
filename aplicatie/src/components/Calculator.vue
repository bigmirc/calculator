<template>
  <div class="calculator">
    <div class="display">{{result || '0'}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="plus" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
export default {
data() {
    return {
      previous: null,
      result: '',
      operator: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.result = '';
    },
    sign() {
      this.result = this.result.charAt(0) === '-' ? 
        this.result.slice(1) : `-${this.result}`;
    },
    percent() {
      this.result = `${parseFloat(this.result) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.result = '';
        this.operatorClicked = false;
      }
      this.result = `${this.result}${number}`;
    },
    dot() {
      if (this.result.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.result;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.result = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.result),
      )}`;
      this.previous = null;
    }
  }
}
</script>

<!-- add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.calculator{
  margin-left:474.5px ;
  margin-top:3px;
  width: 743px;
  font-size: 70px;
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(50px,auto);
}

.display{
  grid-column: 1 / 5;
  background-color: rgb(39, 39, 39);
  color: white;
}

.btn{
  color: rgb(39, 39, 39);
  background-color: #F2F2F2;
  border: 2px solid rgb(165, 165, 165);
  transition: 0.3s;
  cursor:pointer
}

.btn:active {
  background-color: #e0dddd;

}

.zero{
  grid-column: 1 / 3;
}

.operator{
  background-color:salmon;
  color:white;
}

</style>
