<template>
  <NuxtLink :to="`/box/${box.id}`" class="p-2 flex flex-col cursor-pointer">
    <div class="w-full aspect-square overflow-hidden rounded-lg bg-gray-200">
      <img :src="box.image || 'https://picsum.photos/400/400'" alt="Box" class="w-full h-full object-cover"/>
    </div>
    <div class="mt-2 text-sm">
      <div class="flex justify-between items-center">
        <h2 class="text-base font-bold">{{ box.name || "Nom de la box" }}</h2>
        <span class="flex items-center"><img src="/images/star.svg" alt="Star Rating" class="h-3 mr-1 -mt-1">{{ box.rating || "0,00" }}</span>
      </div>
      <p class="text-gray-500">{{ box.owner_name || "Non renseigné" }}</p>
      <p class="text-gray-400">Dates d’intentées disponnibles</p>
      <p class="font-semibold mt-1">{{ box.price ? `${parseFloat(box.price).toFixed(2)}€` : "0,00€" }}/nuit</p>
    </div>
  </NuxtLink>
</template>

<script setup>
defineProps({
  box: {
    type: Object,
    required: true
  }
});
</script>
