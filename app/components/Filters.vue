<template>
    <div class="flex items-center justify-end my-6">
      <button @click="isOpen = true" class="border p-2 rounded flex items-center gap-2 font-bold">
        <span><img src="/images/filter.svg" alt="Horscape Logo" class="h-5"></span> Filtres
      </button>
      
      <div v-if="isOpen" class="fixed inset-0 bg-gray-900 bg-opacity-50 flex justify-center items-center">
        <div class="bg-white rounded-lg w-11/12 max-w-md p-4 shadow-lg">
          <div class="flex justify-between items-center border-b pb-2">
            <h3 class="text-lg font-bold">Filtres</h3>
            <button @click="isOpen = false" class="text-gray-500">&times;</button>
          </div>
          
          <div class="mt-4 space-y-4">
            <div>
              <h4 class="text-sm font-semibold">Type de logement</h4>
              <div class="flex flex-wrap gap-2 mt-2">
                <button class="border px-3 py-1 rounded-full">Tous les types</button>
                <button class="border px-3 py-1 rounded-full">Box avec paddock</button>
                <button class="border px-3 py-1 rounded-full">Paddock individuel</button>
                <button class="border px-3 py-1 rounded-full">Pré avec abri</button>
                <button class="border px-3 py-1 rounded-full">Stabulation libre</button>
              </div>
            </div>
    
            <div>
              <h4 class="text-sm font-semibold">Dimensions du box</h4>
              <div class="flex gap-2 mt-2">
                <button class="border px-3 py-1 rounded-full">3×3m</button>
                <button class="border px-3 py-1 rounded-full">4×4m</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "FilterModal",
    data() {
      return {
        isOpen: false
      };
    }
  };
  </script>
  
  <style scoped>
  button {
    transition: background 0.2s ease-in-out;
  }
  button:hover {
    background: #f3f4f6;
  }
  </style>
  