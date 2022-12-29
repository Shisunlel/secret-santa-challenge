<script setup>
import { ref } from 'vue'

const active = ref(0)
const cssClass = ref({
  0: 'left-0 z-10 rotate-0',
  1: 'left-[-10px] z-0 rotate1',
  2: 'left-[10px] z-0 rotate2',
})
function setActive(evt) {
  active.value = evt.target.dataset.index
  if (evt.target.dataset.index === '0') {
    cssClass.value = {
      0: 'left-0 z-10 rotate-0',
      1: 'left-[-10px] z-0 rotate1',
      2: 'left-[10px] z-0 rotate2',
    }
  } else if (evt.target.dataset.index === '1') {
    cssClass.value = {
      0: 'left-[-10px] z-0 rotate1',
      1: 'left-0 z-10 rotate-0',
      2: 'left-[10px] z-0 rotate2',
    }
  } else if (evt.target.dataset.index === '2') {
    cssClass.value = {
      0: 'left-[-10px] z-0 rotate1',
      1: 'left-[10px] z-0 rotate2',
      2: 'left-0 z-10 rotate-0',
    }
  }
}
</script>
<template>
  <div class="relative flex mt-12 min-h-[270px] left-[15%]">
    <div data-index="0" class="bg-blue-500 card" :class="[cssClass[0]]" @click.prevent="setActive">
      <span class="card-content">I love watching anime; my favorite anime is Doctor Stone</span>
    </div>
    <div data-index="1" class="bg-lime-500 card" :class="[cssClass[1]]" @click.prevent="setActive">
      <span class="card-content">I am a Frontend Developer</span>
    </div>
    <div data-index="2" class="bg-indigo-500 card" :class="[cssClass[2]]" @click.prevent="setActive">
      <span class="card-content">I love to be alone</span>
    </div>
  </div>
</template>
<style scoped>
.card {
  @apply transition-all rounded-lg absolute w-52 h-60 p-8 flex justify-center items-center text-white;
}

.card-content {
  @apply first-letter:capitalize first-letter:bg-clip-text first-letter:bg-gradient-to-t first-letter:from-violet-500 first-letter:to-fuchsia-500 first-letter:text-transparent first-letter:text-2xl;
}

.rotate1 {
  transform: rotate(-10deg);
}

.rotate2 {
  transform: rotate(10deg);
}
</style>
