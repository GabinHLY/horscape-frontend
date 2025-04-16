<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-4 text-center text-[#0F5B55]">LA RÉSERVATION DE BOX EN UN CLIC</h1>
    <h2 class="text-lg font-regular mb-6 text-center">Simplifiez vos déplacements équestres avec une solution digitale pensée pour le bien-être animal</h2>

    <SearchBar />
    <div class="w-full border-b border-gray-300 my-6"></div>
    <Filters />

    <div class="fixed bottom-24 left-1/2 transform -translate-x-1/2 z-50">
      <MapButton />
    </div>

    <!-- Affichage des boxes avec "Afficher plus" -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-5">
      <template v-for="(box, index) in paginatedBoxesWithImages" :key="box.id">
        <BoxCard v-if="index < 8 || showMore" :box="box" class="transform scale-[0.98]" />
      </template>
    </div>

    <!-- Bouton "Afficher plus" -->
    <div v-if="!showMore && paginatedBoxesWithImages.length > 8" class="flex justify-center mt-4">
      <button @click="showMore = true" class="px-4 py-2 bg-[#0F5B55] text-white font-medium rounded">Afficher plus</button>
    </div>

    <!-- Résultats + pagination alignée à droite -->
    <div class="flex justify-between items-center mt-8">
      <p class="text-sm text-gray-500">
        <span class="font-semibold text-black">{{ boxes.length }}</span> résultats
      </p>

      <div v-if="totalPages > 1" class="flex items-center space-x-2 text-[#0F5B55] font-medium">
        <button 
          @click="prevPage"
          :disabled="currentPage === 1"
          class="disabled:opacity-30 disabled:cursor-not-allowed"
        >
          &lt;
        </button>

        <span class="w-8 h-8 flex items-center justify-center rounded-md bg-[#E8F1EF] text-black font-semibold">
          {{ currentPage }}
        </span>

        <span class="text-gray-500 text-sm">sur</span>
        <span class="text-black font-semibold text-sm">{{ totalPages }}</span>

        <button 
          @click="nextPage"
          :disabled="currentPage === totalPages"
          class="disabled:opacity-30 disabled:cursor-not-allowed"
        >
          &gt;
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, watchEffect } from 'vue';
import Filters from '@/components/Filters.vue';
import BoxCard from '@/components/BoxCard.vue';
import SearchBar from '@/components/SearchBar.vue';

const { data: boxesRaw } = await useFetch(
  () => `${useRuntimeConfig().public.NUXT_PUBLIC_API_BASE}/boxes`
);

console.log('boxes', boxesRaw)

const boxes = ref([]);
if (boxesRaw.value) {
  boxes.value = boxesRaw.value;
}

// Pagination
const itemsPerPage = 16;
const currentPage = ref(1);
const showMore = ref(false);
const totalPages = computed(() => Math.ceil(boxes.value.length / itemsPerPage));

const changePage = (page: number) => {
  currentPage.value = page;
  showMore.value = false;
  scrollToTop();
};

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    changePage(currentPage.value + 1);
  }
};

const prevPage = () => {
  if (currentPage.value > 1) {
    changePage(currentPage.value - 1);
  }
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
};

// Attribution d'images locales aléatoires
const boxesWithImages = ref([]);

const getRandomImageMap = (boxesLength: number) => {
  const imageIndexes = Array.from({ length: 16 }, (_, i) => i + 1);
  const shuffled = imageIndexes.sort(() => Math.random() - 0.5);
  return shuffled.slice(0, boxesLength).map(i => `/images/ecuries/${i}.jpg`);
};

watchEffect(() => {
  if (boxes.value.length > 0) {
    const randomImages = getRandomImageMap(boxes.value.length);
    boxesWithImages.value = boxes.value.map((box, index) => ({
      ...box,
      image: box.image || randomImages[index]
    }));
  }
});

const paginatedBoxesWithImages = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  return boxesWithImages.value.slice(start, start + itemsPerPage);
});
</script>
