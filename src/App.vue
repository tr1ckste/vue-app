<template>
  <input
    v-model="counterFromInput"
    type="number"
    @keypress.enter="writeDownInput"
    >
  <div
  class="counter" 
  :class="{
    'green-color': counter % 5 === 0,
    'red-color': counter % 3 === 0 
  }"
  >
    counter: {{ counter }}
  </div>
  <div class="buttons">
    <button
    :disabled="counter === maxValue"
    class="green-bg"
    id="plus"
    @click="plus"
    >+</button>
    <button
    :disabled="counter === minValue"
    class="red-bg"
    id="minus"
    @click="minus"
    >-</button>
  </div>
  <div>
    <ul>
      <li v-for="(element, index) in array" :key="index">
        array {{ element }}
      </li>
    </ul>
  </div>
  <div>
    <ul>
      <li v-for="(value, key) in object" :key="key">
        object value: {{ value }}, object key: {{ key }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      maxValue: 20,
      minValue: 0,
      counter: 0,
      counterFromInput: null,
      array: [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
      ],
      object: {
        first: 1,
        second: 2,
        third: 3,
        fourth: 4,
        fifth: 5,
      },
    };
  },
  methods: {
    plus() {
      const condition = this.counter === this.maxValue;
      if (condition) return;
      this.counter++;
    },
    minus() {
      const condition = this.counter === this.minValue;
      if (condition) return;
      this.counter--;
    },
    writeDownInput() {
      const num = this.counterFromInput;
      const { maxValue, minValue } = this;
      if (num <= maxValue && num >= minValue) this.counter = num;
      this.counterFromInput = 0;
    }
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
}

.buttons > button {
  padding: 10px 50px;
  margin: 10px;
}

.green-bg {
  background: green;
}

.red-bg {
  background: red;
}

.green-color {
  color: green;
}

.red-color {
  color: red;
}

</style>
