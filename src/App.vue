<template>
  <div id="app">
    <div class="container">
    <div class="result-display">
      <!-- <strong> -->
      {{ number1 }}
      {{ calculationType }}
      {{ number2 }}
      <!-- </strong> -->
    </div>
    <br>
    <div class="columns">
      <div class="column col-3">
        <div class="app-button">
        <button @click="add">+</button>
        </div>
      </div>
      <div class="column col-3">
        <div class="app-button">
        <button @click="subtract">-</button>
        </div>
      </div>
      <div class="column col-3">
        <div class="app-button">
        <button @click="multiply">*</button>
        </div>
      </div>
      <div class="column col-3">
        <div class="app-button">
        <button @click="divide">/</button>
        </div>
      </div>
    <div class="column col-3"
    v-for="number in buttonNumbers">
    <div class="app-button">
      <app-button
      :number="number"
      @parentClicked="enterNumber"
      ></app-button>
    </div>
    </div>
    <div class="column col-3">
    <div class="app-button">
    <button @click="calculation">=</button>
    </div>
    </div>
    <div class="column col-3">
      <div class="app-button">
      <button @click="clear">C</button>
      </div>
    </div>
    </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Button from './components/Button.vue';

export default Vue.extend({
  name: 'app',
  components: {
    'appButton': Button,
  },
  data() {
    return {
      number1: '',
      number2: '',
      buttonNumbers: [1,2,3,4,5,6,7,8,9,0],
      calculationType: ''
    }
  },
  methods: {
    calculation() {
      if (this.calculationType === '+') {
        this.number1 = Number(this.number1) + Number(this.number2)
      }
      else if (this.calculationType === '-') {
        this.number1 = Number(this.number1) - Number(this.number2)
      }
      else if (this.calculationType === '*') {
        this.number1 = Number(this.number1) * Number(this.number2)
      }
      else if (this.calculationType === '/') {
        this.number1 = Number(this.number1) / Number(this.number2)
      }
      this.number2 = ''
      this.calculationType = ''
    },
    add() {
      if (this.number2) {
        this.calculation()
      }
      if (this.number1) {
        this.calculationType = '+'
      }
    },
    subtract() {
      if (this.number2) {
        this.calculation()
      }
      if (this.number1) {
        this.calculationType = '-'
      }
    },
    multiply() {
      if (this.number2) {
        this.calculation()
      }
      if (this.number1) {
        this.calculationType = '*'
      }
    },
    divide() {
      if (this.number2) {
        this.calculation()
      }
      if (this.number1) {
        this.calculationType = '/'
      }
    },
    enterNumber(event) {
      if (!this.calculationType) {
        this.number1 += String(event)
      }
      else {
        this.number2 += String(event)
      }
    },
    clear() {
      this.number1 = ''
      this.number2 = ''
      this.calculationType = ''
    }
  }
});
</script>

<style scoped>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
  margin-top: 60px;
  width: 400px;
  border: 2px solid black;
  border-radius: 7px;
  padding: 15px;
  background-color: #def;
}

.app-button {
  border: 1px solid black;
  border-radius: 10px;
  box-shadow: none;
  width: 65px;
  height: 65px;
  margin: auto;
  background-color: #3f99aa;
  margin-bottom: 13px;
}

.app-button:hover, button:hover {
  cursor: pointer;
}

button {
  background-color: #3f99aa;
  border: none;
  padding-top: 6px;
  border-radius: 10px;
  width: 100%;
  height: 100%;
}

button:focus, button:active {
  outline:none;
}

.result-display {
  background-color: #adf;
  height: 50px;
  border: 1px solid #bbc;
  border-radius: 8px;
  margin: auto;
  padding-top: 13px;
}

</style>
