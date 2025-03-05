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
    <div v-if="!showMore" class="flex justify-center mt-4">
      <button @click="showMore = true" class="border p-2 rounded">Afficher plus</button>
    </div>

    <!-- Pagination -->
    <div class="flex justify-center mt-4 space-x-2">
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

<script setup>
import { ref, computed } from 'vue';
import Filters from '@/components/Filters.vue';
import BoxCard from '@/components/BoxCard.vue';
import SearchBar from '@/components/SearchBar.vue';

const boxes = ref([
  { id: 1, title: 'Box 1', description: 'Description for Box 1', imageUrl: 'https://via.placeholder.com/150' },
  { id: 2, title: 'Box 2', description: 'Description for Box 2', imageUrl: 'https://via.placeholder.com/150' },
  { id: 3, title: 'Box 3', description: 'Description for Box 3', imageUrl: 'https://via.placeholder.com/150' },
  { id: 4, title: 'Box 4', description: 'Description for Box 4', imageUrl: 'https://via.placeholder.com/150' },
  { id: 5, title: 'Box 5', description: 'Description for Box 5', imageUrl: 'https://via.placeholder.com/150' },
  { id: 6, title: 'Box 6', description: 'Description for Box 6', imageUrl: 'https://via.placeholder.com/150' },
  { id: 7, title: 'Box 7', description: 'Description for Box 7', imageUrl: 'https://via.placeholder.com/150' },
  { id: 8, title: 'Box 8', description: 'Description for Box 8', imageUrl: 'https://via.placeholder.com/150' },
  { id: 9, title: 'Box 9', description: 'Description for Box 9', imageUrl: 'https://via.placeholder.com/150' },
  { id: 10, title: 'Box 10', description: 'Description for Box 10', imageUrl: 'https://via.placeholder.com/150' },
  { id: 11, title: 'Box 11', description: 'Description for Box 11', imageUrl: 'https://via.placeholder.com/150' },
  { id: 12, title: 'Box 12', description: 'Description for Box 12', imageUrl: 'https://via.placeholder.com/150' },
  { id: 13, title: 'Box 13', description: 'Description for Box 13', imageUrl: 'https://via.placeholder.com/150' },
  { id: 14, title: 'Box 14', description: 'Description for Box 14', imageUrl: 'https://via.placeholder.com/150' },
  { id: 15, title: 'Box 15', description: 'Description for Box 15', imageUrl: 'https://via.placeholder.com/150' },
  { id: 16, title: 'Box 16', description: 'Description for Box 16', imageUrl: 'https://via.placeholder.com/150' },
  { id: 17, title: 'Box 17', description: 'Description for Box 17', imageUrl: 'https://via.placeholder.com/150' },
  { id: 18, title: 'Box 18', description: 'Description for Box 18', imageUrl: 'https://via.placeholder.com/150' },
  { id: 19, title: 'Box 19', description: 'Description for Box 19', imageUrl: 'https://via.placeholder.com/150' },
  { id: 20, title: 'Box 20', description: 'Description for Box 20', imageUrl: 'https://via.placeholder.com/150' },
  { id: 21, title: 'Box 21', description: 'Description for Box 21', imageUrl: 'https://via.placeholder.com/150' },
  { id: 22, title: 'Box 22', description: 'Description for Box 22', imageUrl: 'https://via.placeholder.com/150' },
  { id: 23, title: 'Box 23', description: 'Description for Box 23', imageUrl: 'https://via.placeholder.com/150' },
  { id: 24, title: 'Box 24', description: 'Description for Box 24', imageUrl: 'https://via.placeholder.com/150' },
  { id: 25, title: 'Box 25', description: 'Description for Box 25', imageUrl: 'https://via.placeholder.com/150' },
  { id: 26, title: 'Box 26', description: 'Description for Box 26', imageUrl: 'https://via.placeholder.com/150' },
  { id: 27, title: 'Box 27', description: 'Description for Box 27', imageUrl: 'https://via.placeholder.com/150' },
  { id: 28, title: 'Box 28', description: 'Description for Box 28', imageUrl: 'https://via.placeholder.com/150' },
  { id: 29, title: 'Box 29', description: 'Description for Box 29', imageUrl: 'https://via.placeholder.com/150' },
  { id: 30, title: 'Box 30', description: 'Description for Box 30', imageUrl: 'https://via.placeholder.com/150' },
  { id: 31, title: 'Box 31', description: 'Description for Box 31', imageUrl: 'https://via.placeholder.com/150' },
  { id: 32, title: 'Box 32', description: 'Description for Box 32', imageUrl: 'https://via.placeholder.com/150' }
]);

const itemsPerPage = 16;
const currentPage = ref(1);
const showMore = ref(false);

const totalPages = computed(() => Math.ceil(boxes.value.length / itemsPerPage));

const paginatedBoxes = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  return boxes.value.slice(start, start + itemsPerPage);
});

const changePage = (page) => {
  currentPage.value = page;
  showMore.value = false;
  scrollToTop();
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
};
</script>
