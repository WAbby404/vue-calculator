<script setup>
import { ref } from "vue";

// this is also the input
// when 1 number is added, add a space, then expect ONLY
// any of the + - / or *
// then expect any number
// when computeResults runs, replace input with the result
const bothNumbers = ref("");

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

const inputNumber = () => {};
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
