<template>
  <div id="app">
    <div class="container">
    <div class="result-display">
      {{ formula }}
      <br>
      <hr>
      <strong>
      {{ result }}
      </strong>
    </div>
    <br>
    <div class="columns">
      <app-button
        class="operator" digit="(" @parentClicked="enter"></app-button>
      <app-button
        class="operator" digit=")" @parentClicked="enter"></app-button>
      <app-button
        class="operator" digit="C" @parentClicked="clear"></app-button>
      <app-button
        class="operator" digit="del" @parentClicked="deleteDigit"></app-button>
      <app-button digit="1" @parentClicked="enter"></app-button>
      <app-button digit="2" @parentClicked="enter"></app-button>
      <app-button digit="3" @parentClicked="enter"></app-button>
      <app-button
        class="operator" digit="+" @parentClicked="enter"></app-button>
      <app-button digit="4" @parentClicked="enter"></app-button>
      <app-button digit="5" @parentClicked="enter"></app-button>
      <app-button digit="6" @parentClicked="enter"></app-button>
      <app-button
        class="operator" digit="÷" @parentClicked="enter"></app-button>
      <app-button digit="7" @parentClicked="enter"></app-button>
      <app-button digit="8" @parentClicked="enter"></app-button>
      <app-button digit="9" @parentClicked="enter"></app-button>
      <app-button
        class="operator" digit="*" @parentClicked="enter"></app-button>
      <app-button class="zero-button"
        digit="0" @parentClicked="enter"></app-button>
      <app-button
        digit="." @parentClicked="enter"></app-button>
      <app-button
        class="operator" digit="/" @parentClicked="enter"></app-button>
      <app-button
        class="operator long-button" digit="=" @parentClicked="calculate"></app-button>
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
      formula: '',
      result: '',
    }
  },

  methods: {

    enter(event: String) {
      this.formula += event
    },

    calculate() {
      this.result = eval(this.formula.replace("÷", "/"))
    },

    clear() {
      this.formula = ''
      this.result = ''
    },

    deleteDigit() {
      this.formula = this.formula.substring(
        0, this.formula.length - 1)
    }
  }

})
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

.result-display {
  background-color: #adf;
  height: 80px;
  border: 1px solid #bbc;
  border-radius: 8px;
  margin: auto;
  padding-top: 13px;
  text-align: right;
}

strong {
  margin-right: 5px;
  padding-top: 15px;
}

.zero-button {
  width: 165px;
}

.long-button {
  width: 350px;
}

hr {
  border: solid #cce .5px;
  margin-bottom: 2px;
}

.operator {
  background-color: lightblue;
}

</style>
