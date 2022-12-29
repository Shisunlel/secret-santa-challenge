<script setup>
import { ref } from 'vue';
import AppHeader from './components/AppHeader.vue'
const guess = ref('')
const isDisable = ref(false);
const onSubmit = () => {
  isDisable.value = true;
  if (guess.value === 'Rapol') {
    alert('You are correct')
    guess.value = ''
    isDisable.value = false;
    return
  }
  alert('Please try again in a moment !!')
  setTimeout(() => {
    isDisable.value = false;
  }, 1000);
}
</script>
<template>
  <div class="w-full h-full flex justify-center items-center p-10">
    <div class="shadow-md relative bg-white p-5 rounded-lg border-gray-100 border-[1px]">
      <p class="text-center">Guess Who's This !</p>
      <AppHeader />
      <div class="flex gap-2">
        <input v-model="guess" class="border border-indigo-300 px-2 py-1 rounded focus:rign-indigo-300" type="text" />
        <button :disabled="isDisable" @click="onSubmit" class="bg-lime-500 px-2 rounded-lg text-white hover:bg-lime-700 disabled:grayscale disabled:cursor-wait">Guess</button>
      </div>
      <h4 class="mt-10 text-gray-400 text-center text-sm">
        This challenge brought to you by <a href="https://vueschool.io/" class="underline">Vue School</a>
      </h4>
    </div>
  </div>
</template>
<style>
div {
  display: block;
}

body {
  @apply bg-gray-100;
}
</style>
