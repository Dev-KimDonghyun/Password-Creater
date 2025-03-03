<template>

<div class="mainContainer">
  <input class="inputHolder" @keydown="enterKeydown" v-model.trim="inputValue" placeholder="Please enter the desired length between 10 and 100">
  <p class="entered">Entered length: {{ inputValue }}</p>
  <button class="inputButton" @click="inputBtn">Create</button>
  <div class="resultContainer">
    <p class="resultHolderPlace">Result: {{ resultHolder }}</p>
  </div>
</div>

</template>

<script setup>

import { ref } from 'vue';

let inputValue = ref('');
let resultHolder = ref('');


const baseString = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789abcdefghijklmnopqrstuvwxyz';


function inputBtn () {

  const inputValueNum = Number(inputValue.value);

  if (inputValue.value === '') {
    alert('Please enter a value');
  } else if (isNaN(inputValueNum)) {
    alert('Please enter a number of 10 or more');
  } else if (inputValueNum < 10) {
    alert('Please enter a number of 100 or less');
  } else if (inputValueNum > 100) {
    alert('Please enter a number');
  } else {
    let resultPW = '';
    for (let i = 0; i < inputValueNum; i ++) {
      let randomNum = Math.floor(Math.random() * (baseString.length));
      resultPW += baseString[randomNum];
    }
    console.log(resultPW); // console.log for test
    resultHolder.value = resultPW;
  }
}

function enterKeydown (event) {
  if (event.key === 'Enter') {
    inputBtn();
  }
}

</script>

<style scoped>

</style>
