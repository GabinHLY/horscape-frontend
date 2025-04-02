<template>
  <nav class="flex items-center justify-between px-12 py-6 bg-white border-b border-gray-300 md:px-16">
    <!-- Logo -->
    <div class="flex items-center">
      <nuxt-link to="/">
        <img src="/images/logo1.svg" alt="Horscape Logo" class="h-10">
      </nuxt-link>
    </div>

    <!-- Menu Desktop -->
    <div class="hidden md:flex items-center space-x-6">
      <div class="flex items-center space-x-3 mr-10">
        <button class="text-base font-medium text-gray-900">Mettre mon box sur Horscape</button>
        <span class="text-lg">
            <img src="/images/vectors.svg" alt="Horscape Logo" class="h-5">
        </span>
      </div>
      <button class="px-4 py-2 border border-[#0F5B55] rounded text-gray-800 text-base">Se connecter</button>
      <button class="px-4 py-2 bg-[#0F5B55] text-white rounded text-base">S'inscrire</button>
    </div>

    <!-- Icône Menu Mobile -->
    <button @click="toggleMenu" class="md:hidden focus:outline-none">
      <svg v-if="!isMenuOpen" class="w-8 h-8" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="black">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
      </svg>
      <svg v-else class="w-8 h-8 text-gray-900" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <!-- Menu Mobile -->
    <div v-show="isMenuOpen" class="absolute top-16 left-0 w-full bg-white shadow-md flex flex-col items-center space-y-5 py-5 md:hidden">
      <button class="text-base font-medium text-gray-900">Mettre mon box sur Horscape</button>
      <button class="px-4 py-2 border border-gray-400 rounded text-gray-800 text-base">Se connecter</button>
      <button class="px-4 py-2 bg-gray-800 text-white rounded text-base">S'inscrire</button>
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
  min-height: 64px;
}
</style>
