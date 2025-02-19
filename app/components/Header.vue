<script setup>
</script>

<template>
  <header class="w-full bg-white shadow-md p-4 flex items-center justify-between">
    <!-- Logo -->
    <div class="text-lg font-bold text-gray-800">
      Horscape
    </div>

    <!-- Barre de recherche -->
    <div class="flex items-center bg-gray-100 p-2 rounded-full w-full max-w-xl">
      <input
        type="text"
        placeholder="Rechercher une destination"
        class="bg-transparent outline-none flex-grow px-3 text-gray-700"
      />
      <button class="bg-gray-300 p-2 rounded-full">
        🔍
      </button>
    </div>

    <!-- Boutons Connexion & Inscription -->
    <div class="flex gap-2">
      <button class="px-4 py-2 text-gray-700">Se connecter</button>
      <button class="px-4 py-2 bg-blue-600 text-white rounded-lg">S'inscrire</button>
    </div>
  </header>
</template>
