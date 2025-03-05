<template>
    <div class="w-full flex justify-center">
      <!-- Mobile Version -->
      <div class="md:hidden">
        <button class="flex items-center gap-2 px-4 py-2 border border-black rounded-full">
          <span>Commencer ma recherche</span>
          <Icon name="lucide:search" class="w-5 h-5" />
        </button>
      </div>
  
      <!-- Desktop Version -->
      <div class="hidden md:flex w-full max-w-3xl items-center border border-black rounded-full px-4 py-2">
        <div class="flex flex-col flex-1">
          <label class="text-xs font-semibold">Destination</label>
          <input
            type="text"
            placeholder="Rechercher une destination"
            class="w-full bg-transparent focus:outline-none text-gray-700"
            v-model="search.destination"
          />
        </div>
        <div class="border-l border-gray-300 h-6 mx-2"></div>
        <div class="flex flex-col">
          <label class="text-xs font-semibold">Arrivée</label>
          <input
            type="date"
            class="w-full bg-transparent focus:outline-none text-gray-700"
            v-model="search.arrival"
          />
        </div>
        <div class="border-l border-gray-300 h-6 mx-2"></div>
        <div class="flex flex-col">
          <label class="text-xs font-semibold">Départ</label>
          <input
            type="date"
            class="w-full bg-transparent focus:outline-none text-gray-700"
            v-model="search.departure"
          />
        </div>
        <div class="border-l border-gray-300 h-6 mx-2"></div>
        <div class="flex flex-col">
          <label class="text-xs font-semibold">Chevaux</label>
          <input
            type="number"
            placeholder="Ajouter des chevaux"
            class="w-full bg-transparent focus:outline-none text-gray-700"
            v-model="search.horses"
          />
        </div>
        <button @click="submitSearch" class="ml-4 bg-gray-200 p-2 rounded-full hover:bg-gray-300">
          <Icon name="lucide:search" class="w-5 h-5" />
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const search = ref({
    destination: "",
    arrival: "",
    departure: "",
    horses: null,
  });
  
  const submitSearch = () => {
    console.log("Recherche :", search.value);
    // Ici, tu peux ajouter une redirection ou un appel API
  };
  </script>
  
  <style scoped>
  input::placeholder {
    color: #b0b0b0;
  }
  </style>
  