<script setup>
import { ref } from "vue";

// this is also the input
// when 1 number is added, add a space, then expect ONLY
// any of the + - / or *
// then expect any number
// when computeResults runs, replace input with the result

// NUMBER1 if number 1 had a value,
// next input is an operator, then
// set NUMBER2 to have the next input value
// & dont accept any other text

// numOne, numTwo and operator will reflect the input,
// numbers first typed will go into numOne
// when an operator is added, a space will be put before it in the input,
// and the operator will go into operator
// when another number is typed after, it will go into numTwo
const inputString = ref("");
const numOne = ref(null);
const numTwo = ref(null);
const operator = ref("");

const add = (a, b) => {
  return a + b;
};

const subtract = (a, b) => {
  return a - b;
};

const divide = (a, b) => {
  return a / b;
};

const multiple = (a, b) => {
  return a * b;
};

const computeResult = () => {
  let finalNumber = 100;
  bothNumbers.value = finalNumber;
};

const changeInput = () => {};
</script>

<template>
  <ol>
    <li v-for="index in 10" :key="index">
      <button type="text" @click="bothNumbers = `${bothNumbers}${index}`">
        {{ index }}
      </button>
      <!-- <button type="text" @click="inputNumber(index)">{{ index }}</button> -->
    </li>
  </ol>
  <button type="text" @click="bothNumbers = `${bothNumbers} + `">+</button>
  <button type="text">-</button>
  <button type="text">*</button>
  <button type="text">/</button>
  <form>
    <!-- <form @submit.prevent="computeResult"></form> -->
    <input v-model="bothNumbers" type="text" />

    <button type="submit">></button>
  </form>
</template>

<style scoped></style>
