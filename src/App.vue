<script setup>
import GameCounter from '@/components/GameCounter.vue'

const MIN_NUMBER = 0
const MAX_NUMBER = 50
</script>

<template>
  <div
    class="min-h-screen flex items-center justify-center bg-gradient-to-br from-indigo-900 via-black to-slate-900"
  >
    <GameCounter :min-number="MIN_NUMBER" :max-number="MAX_NUMBER" />
  </div>
</template>

<style scoped></style>
