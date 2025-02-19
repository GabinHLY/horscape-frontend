<script setup>
const locations = [
  { id: 1, name: "Nom de location de box", host: "Nom de l'hôte", price: "0€ par nuit", rating: 0.0 },
  { id: 2, name: "Nom de location de box", host: "Nom de l'hôte", price: "0€ par nuit", rating: 0.0 },
  { id: 3, name: "Nom de location de box", host: "Nom de l'hôte", price: "0€ par nuit", rating: 0.0 },
  { id: 4, name: "Nom de location de box", host: "Nom de l'hôte", price: "0€ par nuit", rating: 0.0 },
  { id: 5, name: "Nom de location de box", host: "Nom de l'hôte", price: "0€ par nuit", rating: 0.0 },
  { id: 6, name: "Nom de location de box", host: "Nom de l'hôte", price: "0€ par nuit", rating: 0.0 },
];
</script>

<template>
  <div class="min-h-screen bg-gray-100">
    
    <main class="max-w-6xl mx-auto p-4">
      <!-- Filtres et Recherche -->
      <div class="flex items-center justify-between mb-6">
        <div class="w-full flex bg-white p-3 rounded-lg shadow">
          <input
            type="text"
            placeholder="Rechercher une destination"
            class="flex-grow px-4 py-2 outline-none"
          />
          <input type="date" class="px-4 py-2 border-l outline-none" />
          <input type="date" class="px-4 py-2 border-l outline-none" />
          <input type="text" placeholder="Ajouter des chevaux" class="px-4 py-2 border-l outline-none" />
          <button class="px-4 py-2 bg-blue-600 text-white rounded-md">🔍</button>
        </div>
        <button class="ml-4 px-4 py-2 bg-gray-200 rounded-lg">Filtres</button>
      </div>

      <!-- Grille des locations -->
      <div class="grid grid-cols-3 gap-6">
        <NuxtLink
            v-for="location in locations"
            :key="location.id"
            :to="`/location/${location.id}`"
            class="bg-white p-4 rounded-lg shadow-md hover:shadow-xl transition-all"
        >

          <div class="h-40 bg-gray-300 rounded-lg"></div>
          <h3 class="text-lg font-semibold mt-2">{{ location.name }}</h3>
          <p class="text-gray-600 text-sm">{{ location.host }}</p>
          <p class="text-gray-500 text-sm">Dates de disponibilités disponibles</p>
          <p class="font-bold mt-2">{{ location.price }}</p>
        </NuxtLink>
      </div>

      <!-- Bouton Afficher la Carte -->
      <div class="fixed bottom-10 left-1/2 transform -translate-x-1/2 bg-black text-white px-6 py-3 rounded-full shadow-lg">
        Afficher la carte
      </div>
    </main>
  </div>
</template>

