<template>
  <nav class="flex items-center justify-between px-4 py-2 bg-white shadow-md md:px-6">
    <!-- Logo -->
    <div class="text-lg font-bold text-gray-900">Horscape</div>

    <!-- Menu Desktop -->
    <div class="hidden md:flex items-center space-x-4">
      <div class="flex items-center space-x-2 mr-8">
        <button class="text-sm font-medium text-gray-900">Mettre mon box sur Horscape</button>
        <span class="text-gray-600">&#x1F310;</span>
      </div>
      <button class="px-3 py-1 border border-gray-400 rounded text-gray-800">Se connecter</button>
      <button class="px-3 py-1 bg-gray-800 text-white rounded">S'inscrire</button>
    </div>

    <!-- Icône Menu Mobile -->
    <button @click="toggleMenu" class="md:hidden focus:outline-none">
      <svg v-if="!isMenuOpen" class="w-6 h-6 text-gray-900" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
      </svg>
      <svg v-else class="w-6 h-6 text-gray-900" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <!-- Menu Mobile -->
    <div v-show="isMenuOpen" class="absolute top-14 left-0 w-full bg-white shadow-md flex flex-col items-center space-y-4 py-4 md:hidden">
      <button class="text-sm font-medium text-gray-900">Mettre mon box sur Horscape</button>
      <button class="px-3 py-1 border border-gray-400 rounded text-gray-800">Se connecter</button>
      <button class="px-3 py-1 bg-gray-800 text-white rounded">S'inscrire</button>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<style scoped>
nav {
  min-height: 56px;
}
</style>
