<template>

</template>

<script setup>

const baseString = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789abcdefghijklmnopqrstuvwxyz'

function mainFunction () {
  let resultPW = '';
  for (let i = 0; i < 10; i ++) {
    let randomNum = Math.floor(Math.random() * (baseString.length));
    resultPW += baseString[randomNum];
  }
  console.log(resultPW);
}

mainFunction();

</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
