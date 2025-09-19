<script setup>
import { ref } from 'vue'

const counter = ref(0)

const increment = () => {
  counter.value++
}

const decrement = () => {
  counter.value--
}

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

console.log(minNumber, maxNumber)
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
        @click="decrement"
      >
        -
      </button>
      <button
        class="bg-lime-500 hover:bg-lime-600 text-white font-extrabold py-2 px-4 rounded-xl text-2xl"
        @click="increment"
      >
        +
      </button>
    </div>
  </div>
</template>

<style scoped></style>
