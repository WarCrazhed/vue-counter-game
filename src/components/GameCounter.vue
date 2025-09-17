<script setup>
  const isActive = false;
</script>

<template>
  <button>menos</button>
  <span class="counter" :class="{ 'counter--active': isActive }" style="font-size: 4rem;">Contador: 0</span>
  <button>más</button>
</template>

<style scoped>
  .counter {
    font-weight: bold;
    font-size: 2rem;
  }

  .counter--active {
    color: aqua;
  }

  button {
    background-color: red; /* Green */
  }
</style>
