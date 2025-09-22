<script setup>
import { computed, ref, watch } from 'vue'
import JSConfetti from 'js-confetti'
import { getRandomNumbers } from '@/utils/randomNumbers'

const { minNumber, maxNumber } = defineProps({
  minNumber: {
    type: Number,
    required: true,
  },
  maxNumber: {
    type: Number,
    required: true,
  },

  example: {
    type: Object,
    default: () => ({
      name: 'Mario',
    }),
  },
})

const { initialRandomNumber, numberToGuess } = getRandomNumbers({ maxNumber, minNumber })
const jsConfetti = new JSConfetti()

const counter = ref(initialRandomNumber)
const win = ref(false)

const increment = () => {
  if (maxNumber === counter.value) return
  counter.value++
}

const decrement = () => {
  if (counter.value === 0) return
  counter.value--
}

watch(counter, () => {
  if (counter.value === numberToGuess) {
    jsConfetti.addConfetti()
    win.value = true
  }
})

const styleButton = computed(() => {
  return win.value ? 'background: gray; disabled: true' : 'cursor: pointer'
})

const isMax = computed(() => counter.value < numberToGuess)
const isMin = computed(() => counter.value > numberToGuess)
</script>

<template>
  <div
    class="text-center flex flex-col items-center gap-5 border border-slate-800 w-2xl mx-5 max-w-6xl p-10 rounded-3xl bg-black/50 backdrop-blur-sm text-white shadow-2xl shadow-indigo-950"
  >
    <p class="text-2xl font-bold mt-5">Guess the number!</p>
    <p class="text-5xl font-bold hover:scale-115 duration-200 ease-in-out mb-10">{{ counter }}</p>
    <div class="flex gap-2 justify-center">
      <button
        class="bg-red-500 hover:bg-red-600 text-white font-extrabold py-2 px-4 rounded-xl text-2xl"
        :style="styleButton"
        :disabled="win"
        @click="decrement"
      >
        -
      </button>
      <button
        class="bg-lime-500 hover:bg-lime-600 text-white font-extrabold py-2 px-4 rounded-xl text-2xl }}"
        :style="styleButton"
        :disabled="win"
        @click="increment"
      >
        +
      </button>
    </div>
    <p v-if="isMax">Buscar número mayor</p>
    <p v-else-if="isMin">Buscar número menor</p>
    <p v-else-if="win">¡Has ganado!</p>
  </div>
</template>

<style scoped></style>
