<script setup lang="ts">
  const symbols = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "A", "B", "C", "D", "E", "F"];
  const getRandomHex = () => symbols[Math.floor(Math.random() * symbols.length)];

  const currentColor = ref("000000");

  const handleColorChange = () => {
    let newColor = "";

    for (let i = 0; i < 6; i++) {
      newColor += getRandomHex();
    }

    currentColor.value = newColor;
  }

  watch(currentColor, () => {
    console.log(currentColor.value);
  })
</script>

<template>
  <div class="wraper" :style="{ 'background-color': '#' + currentColor }">
    <div class="color" :style="{ 'color': '#' + currentColor }">
      #<input v-model="currentColor" max="6" maxlength="6" :style="{ 'color': '#' + currentColor }">
    </div>
    <button class="color" :style="{ 'color': '#' + currentColor }" @click="handleColorChange">Losuj Kolorek!</button>
  </div>
</template>

<style>
  .wraper {
    height: 100vh;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 2rem;
    flex-direction: column;
  }

  .wraper > div.color {
    background-color: white;
    padding: 2rem;
    border-radius: 1rem;
    font-size: 4rem;
    display: flex;
    width: min-content;
    align-items: center;
    justify-content: center;
  }
  .wraper > button.color {
    background-color: white;
    padding: 2rem;
    border-radius: 1rem;
    font-size: 2rem;
    outline: none;
    border: none;
  }

  .wraper input {
    border: none;
    outline: none;
    font-size: 4rem;
    width: 20rem;
    text-transform: uppercase;
  }

  @media (max-width: 800px) {
    .wraper > div.color {
      font-size: 2rem;
      padding: 1rem;
    }
    .wraper > button.color {
      font-size: 1.25rem;
      padding: 1rem;
    }

    .wraper input {
      font-size: 2rem;
      width: 12rem;
    }
  }
</style>
``