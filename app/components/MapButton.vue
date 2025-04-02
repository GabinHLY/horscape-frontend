<template>
    <button
      class="flex items-center gap-2 bg-custom-green px-4 py-2 rounded-full shadow-lg transition-transform hover:scale-105 min-w-max"
      @click="handleButtonClick"
    >
      <span class="text-white font-medium whitespace-nowrap">Afficher la carte</span>
      <img src="/images/ping.svg" alt="Horscape Logo" class="h-5" />
    </button>
  </template>
  
  <script setup>
  // const handleButtonClick = () => { ... }
  </script>
  
  <style scoped>
  .bg-custom-green {
    background-color: #0F5B55;
  }
  </style>
  