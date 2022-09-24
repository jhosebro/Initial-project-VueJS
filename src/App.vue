<script setup>
import {ref} from 'vue';

const name = 'Hello Jhosebro'
const styleColor = 'color: green';
const styleColorRed = 'color: red';
const styleColorWhite = 'color: white';

const arrayColors = ['red', 'green', 'blue'];
const active = true;
const fruitsArray = ['🍎', '🍌', '🍉', '🍇', '🍓', '🍍'];
const priceList = [
  { name: 'Apple', price: 10, description: 'An apple' },
  { name: 'Banana', price: 20, description: 'A banana'},
  { name: 'Orange', price: 30, description: 'An orange'},
  { name: 'Grape', price: 40, description: 'A Grape' },
  { name: 'Strawberry', price: 50, description: 'An strawberry' },
  { name: 'Pineapple', price: 60, description: 'An pineapple'},
];
const personObject = { name: 'Jhosebro', age: 25, hobby: 'Programming' };

const handleClick = () => {
  console.log('You clicked me!');
}

const counter = ref(0);

const increment = () => {
  counter.value++;
}

const decrement = () => {
  counter.value--;
}

const reset = () => {
  counter.value = 0;
}

</script>

<template>
  <h1>{{ name.toUpperCase() }}</h1>
  <h2 :style="styleColor">{{ arrayColors }}</h2>
  <h2 v-bind:style="`color: ${arrayColors[2]}`"> I'm green</h2>
  <h2 :style="`color: ${arrayColors[0]}`">
    {{ active ? 'Im active' : 'Im not active' }}
  </h2>
  <p v-if="active === true">I'm active</p>
  <p v-else-if="active === false">I'm not active</p>
  <p v-else>I'm undecided</p>
  <ul>
    <li v-for="fruit in fruitsArray" :key="fruit">{{ fruit }}</li>
  </ul>
  <br>
  <ol>
    <li v-for="item in priceList" :key="item.name">
      {{'Fruit: ' + item.name }} / {{'Price: ' + '$' + item.price }} / {{'Description: ' + item.description }}
    </li>
  </ol>
  <br>
  <ul>
    <li v-for="(value, key) in personObject" :key="key">
      {{ key }}: {{ value }}
    </li>
  </ul>
  <br>
  <ul>
    <template v-for="item in priceList" :key="item.name">
      <li v-if="item.price <= 30">{{item.name}}</li>
    </template>
  </ul>
  <br>
  <button @:click="handleClick()">Click me!</button>
  <br>
  <h1>Counter</h1>
  <h1 v-if="counter < 0" :style="styleColorRed">{{ counter }}</h1>
  <h1 v-else-if="counter > 0" :style="styleColor">{{ counter }}</h1>
  <h1 v-else :style="styleColorWhite">{{ counter }}</h1>
  
  
  
  
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
  <button @click="reset">Reset</button>
</template>

<style>
h1 {
  color: springgreen;
}
</style>
