<template>
  <NuxtLink
    :to="box?.id ? `/box/${box.id}` : '#'"
    class="p-2 flex flex-col cursor-pointer"
  >
    <div class="w-full aspect-square overflow-hidden rounded-lg bg-gray-200">
      <img
        :src="safeImage"
        alt="Box"
        class="w-full h-full object-cover"
        loading="lazy"
      />
    </div>
    <div class="mt-2 text-sm">
      <div class="flex justify-between items-center">
        <h2 class="text-base font-bold">{{ box?.name || "Nom de la box" }}</h2>
        <span class="flex items-center">
          <img src="/images/star.svg" alt="Star Rating" class="h-3 mr-1 -mt-1" />
          {{ formattedRating }}
        </span>
      </div>
      <p class="text-gray-500">{{ box?.owner_name || "Non renseigné" }}</p>
      <p class="text-gray-400">Dates d’intentées disponibles</p>
      <p class="font-semibold mt-1">{{ formattedPrice }}/nuit</p>
    </div>
  </NuxtLink>
</template>

<script setup>
const props = defineProps({
  box: {
    type: Object,
    required: true
  }
});

const safeImage = computed(() => {
  return props.box.image?.length
    ? props.box.image
    : '/images/fallback.jpg'; // Assure-toi que ce fichier existe !
});

const formattedRating = computed(() => {
  const rating = props.box.rating
  return rating !== undefined && rating !== null
    ? parseFloat(rating).toFixed(2).replace('.', ',')
    : '0,00';
});

const formattedPrice = computed(() => {
  const price = props.box.price
  return price
    ? `${Number(price).toFixed(2)}€`
    : '0,00€';
});
</script>
