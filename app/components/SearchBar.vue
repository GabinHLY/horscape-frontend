<template>
  <div class="w-full flex justify-center">
    <!-- Version Mobile -->
    <div class="md:hidden">
      <button class="flex items-center gap-2 px-4 py-2 border border-black rounded-full">
        <span>Commencer ma recherche</span>
        <Icon name="lucide:search" class="w-5 h-5" />
      </button>
    </div>

    <!-- Version Desktop -->
    <div
      class="hidden md:flex w-full max-w-5xl items-center rounded-full shadow-sm border border-black px-6 py-3 bg-white gap-x-6"
    >
      <!-- Destination -->
      <div class="flex flex-col flex-1">
        <label class="text-s font-semibold text-gray-800 mb-1">Destination</label>
        <input
          type="text"
          placeholder="Rechercher une destination"
          class="w-full bg-transparent placeholder-gray-400 text-sm focus:outline-none"
          v-model="search.destination"
        />
      </div>

      <!-- Barre de séparation -->
      <div class="h-8 w-[1px] bg-gray-300"></div>

      <!-- Arrivée -->
      <div class="flex flex-col w-[150px]">
        <label class="text-s font-semibold text-gray-800 mb-1">Arrivée</label>
        <input
          type="date"
          class="w-full bg-transparent text-sm focus:outline-none"
          v-model="search.arrival"
        />
      </div>

      <!-- Barre de séparation -->
      <div class="h-8 w-[1px] bg-gray-300"></div>

      <!-- Départ -->
      <div class="flex flex-col w-[150px]">
        <label class="text-s font-semibold text-gray-800 mb-1">Départ</label>
        <input
          type="date"
          class="w-full bg-transparent text-sm focus:outline-none"
          v-model="search.departure"
        />
      </div>

      <!-- Barre de séparation -->
      <div class="h-8 w-[1px] bg-gray-300"></div>

      <!-- Chevaux -->
      <div class="flex flex-col w-[160px]">
        <label class="text-s font-semibold text-gray-800 mb-1">Chevaux</label>
        <input
          type="number"
          placeholder="Ajouter des chevaux"
          class="w-full bg-transparent text-sm placeholder-gray-400 focus:outline-none"
          v-model="search.horses"
        />
      </div>


      <!-- Bouton -->
      <button
        @click="submitSearch"
        class="flex items-center justify-center ml-2 bg-[#0F5B55] hover:bg-[#0a403c] p-3 rounded-full transition duration-200"
      >
        <img src="/images/search.svg" alt="Recherche" class="h-5 w-5" />
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
};
</script>

<style scoped>
input::placeholder {
  color: #b0b0b0;
}
</style>
