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
const numOne = ref("");
const numTwo = ref("");
const operator = ref("");
const result = ref("");

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
  let num = parseInt(numOne.value);
  let nom = parseInt(numTwo.value);

  console.log(num);
  console.log(nom);

  console.log(numOne.value);
  console.log(numTwo.value);

  result.value = num + nom;

  numOne.value = "";
  numTwo.value = "";
  operator.value = "";
};

const changeInput = (input) => {
  // numOne, numTwo and operator will reflect the input,
  // numbers first typed will go into numOne
  // when an operator is added, a space will be put before it in the input,
  // and the operator will go into operator
  // when another number is typed after, it will go into numTwo

  if (typeof input !== "number") {
    operator.value = input;
  } else if (operator.value === "") {
    numOne.value = numOne.value.toString() + input.toString();
  } else {
    numTwo.value = numTwo.value.toString() + input.toString();
  }

  // if (operator.value === "") {
  //   numOne.value = numOne.value.toString() + input.toString();
  // } else if (typeof input !== "number") {
  //   operator.value = input;
  // } else {
  //   numTwo.value = numTwo.value.toString() + input.toString();
  // }
  console.log(numOne.value);
  console.log(numTwo.value);
  console.log(operator.value);
};
</script>

<template>
  <h1>
    {{
      `${numOne === null ? "__" : numOne} ${operator} ${
        numTwo === null ? "__" : numTwo
      }`
    }}
  </h1>
  <h2>{{ result }}</h2>
  <ol>
    <li v-for="index in 10" :key="index">
      <button type="text" @click="changeInput(index)">
        {{ index }}
      </button>
      <!-- <button type="text" @click="inputNumber(index)">{{ index }}</button> -->
    </li>
  </ol>
  <button type="text" @click="changeInput('+')">+</button>
  <button type="text">-</button>
  <button type="text">*</button>
  <button type="text">/</button>
  <br />
  <button type="text" @click="computeResult">CONSULT COMPUTRON</button>
</template>

<style scoped></style>
