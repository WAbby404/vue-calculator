<script setup>
import { ref } from "vue";

const numOne = ref("");
const numTwo = ref("");
const operator = ref("");
const result = ref("");

const computeResult = () => {
  // need to check if all 3 have values before we compute resutls
  // throw error if not
  let num = parseInt(numOne.value);
  let nom = parseInt(numTwo.value);

  if (operator.value === "+") {
    result.value = num + nom;
  } else if (operator.value === "-") {
    result.value = num - nom;
  } else if (operator.value === "*") {
    result.value = num * nom;
  } else {
    result.value = num / nom;
  }

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
  //
  // when someone types an operator after already having a number
  // result needs to be stored in numOne
  // while operator and numTwo are wiped clean
  // if(typeof input === "number"){

  // }
  result.value = "";
  if (typeof input !== "number") {
    operator.value = input;
  } else if (operator.value === "") {
    numOne.value = numOne.value.toString() + input.toString();
  } else {
    numTwo.value = numTwo.value.toString() + input.toString();
  }
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
  <h2 v-show="result.value !== ''">{{ result }}</h2>
  <ol>
    <li v-for="index in 10" :key="index">
      <button type="text" @click="changeInput(index - 1)">
        {{ index - 1 }}
      </button>
      <!-- <button type="text" @click="inputNumber(index)">{{ index }}</button> -->
    </li>
  </ol>
  <button type="text" @click="changeInput('+')">+</button>
  <button type="text" @click="changeInput('-')">-</button>
  <button type="text" @click="changeInput('*')">*</button>
  <button type="text" @click="changeInput('/')">/</button>
  <br />
  <button type="text" @click="computeResult">CONSULT COMPUTRON</button>
</template>

<style scoped></style>
