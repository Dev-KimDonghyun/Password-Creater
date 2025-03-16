<template>

<div class="mainContainer">

  <h1>Password Creater</h1>
  <input class="inputHolder" @keydown="enterKeydown" v-model.trim="inputValue" placeholder="Please enter the desired length between 10 and 100">
  <button class="inputButton" @click="inputBtn">Create</button>
  <div class="resultContainer">
    <p class="resultHolderPlace">{{ resultHolder }}</p>
    <footer>
    <p class="dev">Developed By Kim Donghyun</p>
    </footer>
  </div>
</div>

</template>

<script setup>

import { ref } from 'vue';

let inputValue = ref('');
let resultHolder = ref('The password will be printed here');

const baseString = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789abcdefghijklmnopqrstuvwxyz';


function inputBtn () {

  const inputValueNum = Number(inputValue.value);

  if (inputValue.value === '') {
    alert('Please enter a value');
  } else if (isNaN(inputValueNum)) {
    alert('Please enter a number');
  } else if (inputValueNum < 10) {
    alert('Please enter a number of 10 or more');
  } else if (inputValueNum > 100) {
    alert('Please enter a number of 100 or less');
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

<style scoped >

@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@100..900&display=swap');

body {
  position: relative;
  width: 100%;
}

.mainContainer {
  margin-top: 5%;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%); /* Center Setting */
    height: auto;
    width: 100%;
    text-align: center;
}


h1 {
  margin: 0;
  padding: 0;
  font-family: Lexend;
  font-size: 70px;
  margin-bottom: 20px;
  color: #222831;
  text-shadow: 3px 3px 3px #0e1014, -3px -3px 3px #36404e;
}

.inputHolder {
  width: 500px;
  height: 50px;
  border-top-left-radius: 25px;
  border-bottom-left-radius: 25px;
  border: 0;
  background-color: #EEEEEE;
  text-align: center;
  font-family: Lexend;
  font-size: 17px;
  z-index: 100;
  box-shadow: 8px 7px 5px 0px #121315a6;
  -webkit-box-shadow: 8px 7px 5px 0px #121315a6;
  -moz-box-shadow: 8px 7px 5px 0px #121315a6;
}

.inputHolder:active {
  box-shadow: inset -10px 10px 20px #9b9b9b, inset 10px -10px 20px #ffffff;
}

.inputButton {
  width: 100px;
  height: 50px;
  border-top-right-radius: 25px;
  border-bottom-right-radius: 25px;
  border: 0;
  background-color: #76ABAE;
  font-family: Lexend;
  font-size: 17px;
  color: #31363F ;
  z-index: 100;
  box-shadow: 8px 7px 5px 0px #121315a6;
  -webkit-box-shadow: 8px 7px 5px 0px #121315a6;
  -moz-box-shadow: 8px 7px 5px 0px #121315a6;
}

.inputButton:active {
  box-shadow: inset -10px 10px 20px #4d6f71, inset 10px -10px 20px #9fe7eb;
  color: #5f898b
}

.resultContainer {
  margin-top: 50px;
  font-size: 25px;
  font-family: Lexend;
}

footer {
  position: relative;
  margin-top: 150px;
  padding: 0;
  font-family: Lexend;
  font-size: 20px;
  color: #070a0e;
}

</style>
