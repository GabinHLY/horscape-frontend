<template>
  <NuxtLink :to="`/box/${box.id}`" class="p-2 flex flex-col cursor-pointer">
    <!-- Image de la box -->
    <img 
      :src="box.image || 'https://picsum.photos/200/300'" 
      alt="Box" 
      class="w-full h-40 object-cover rounded-lg bg-gray-200"
    />

    <!-- Informations -->
    <div class="mt-2">
      <div class="flex justify-between items-center">
        <h2 class="text-lg font-bold">{{ box.name || "Nom du location de box" }}</h2>
        <div class="flex items-center">
          <span class="text-black text-sm flex items-center gap-1">
            <p>Note :</p>
            {{ box.rating || "0,00" }}
          </span>
        </div>
      </div>
      <p class="text-sm text-gray-500">Hôte : {{ box.owner_name || "Nom de l’hôte" }}</p>
      <p class="text-sm text-gray-400">{{ box.adress || "Adresse non précisée" }}</p>

      <!-- Prix -->
      <p class="font-semibold mt-1">
        {{ box.price ? `${parseFloat(box.price).toFixed(2)}€` : "0,00€" }} par nuit
      </p>
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
