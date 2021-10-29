<template>
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
    <button class="green-bg" id="plus" v-on:click="plus">+</button>
    <button class="red-bg" id="minus" v-on:click="minus">-</button>
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
      counter: 0,
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
      if (this.counter === 20) return;
      this.counter++;
    },
    minus() {
      if (this.counter === 0) return;
      this.counter--;
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
