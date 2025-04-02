<template>
  <div class="container mx-auto p-4">
    <SearchBar />
    <Filters />

    <!-- Affichage des boxes avec "Afficher plus" -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
      <template v-for="(box, index) in paginatedBoxes" :key="box.id">
        <BoxCard v-if="index < 8 || showMore" :box="box" />
      </template>
    </div>

    <!-- Bouton "Afficher plus" -->
    <div v-if="!showMore && paginatedBoxes.length > 8" class="flex justify-center mt-4">
      <button @click="showMore = true" class="border p-2 rounded">Afficher plus</button>
    </div>

    <!-- Pagination -->
    <div v-if="totalPages > 1" class="flex justify-center mt-4 space-x-2">
      <button 
        v-for="page in totalPages" 
        :key="page"
        @click="changePage(page)"
        class="px-3 py-1 rounded border border-black text-black"
        :class="{ 'bg-black text-white': currentPage === page }"
      >
        {{ page }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import Filters from '@/components/Filters.vue';
import BoxCard from '@/components/BoxCard.vue';
import SearchBar from '@/components/SearchBar.vue';

// Appel API pour récupérer les boxes depuis le backend
const { data: boxesRaw, pending, error } = await useFetch(
  () => `${useRuntimeConfig().public.NUXT_PUBLIC_API_BASE}/boxes`
);

// Réactif car on veut manipuler les données (pagination)
const boxes = ref([]);

if (boxesRaw.value) {
  boxes.value = boxesRaw.value;
}

const itemsPerPage = 16;
const currentPage = ref(1);
const showMore = ref(false);

const totalPages = computed(() => Math.ceil(boxes.value.length / itemsPerPage));

const paginatedBoxes = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  return boxes.value.slice(start, start + itemsPerPage);
});

const changePage = (page: number) => {
  currentPage.value = page;
  showMore.value = false;
  scrollToTop();
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
};
</script>
