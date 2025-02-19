<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();
const locationId = route.params.id;

// Mock des données (à remplacer par une API plus tard)
const locationDetails = {
  id: locationId,
  name: "Nom du location de box",
  host: "Nom de l'hôte",
  rating: 0.0,
  pricePerNight: "0€",
  description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse a tincidunt orci, sit amet porta ipsum.",
  amenities: ["Blablabla", "Blablabla", "Blablabla", "Blablabla"],
  images: ["/placeholder.jpg", "/placeholder.jpg", "/placeholder.jpg"],
};
</script>

<template>
  <div class="min-h-screen bg-gray-100">
    <main class="max-w-6xl mx-auto p-4">
      <!-- Galerie d'images -->
      <div class="grid grid-cols-3 gap-4">
        <div class="col-span-2">
          <img :src="locationDetails.images[0]" alt="Image principale" class="w-full h-64 object-cover rounded-lg shadow-md">
        </div>
        <div class="grid grid-cols-2 gap-4">
          <img v-for="(img, index) in locationDetails.images.slice(1)" :key="index" :src="img" alt="Image secondaire" class="w-full h-32 object-cover rounded-lg shadow-md">
        </div>
      </div>

      <!-- Infos principales -->
      <div class="flex flex-col md:flex-row mt-6">
        <div class="flex-1 pr-6">
          <h1 class="text-2xl font-bold">{{ locationDetails.name }}</h1>
          <p class="text-gray-500 text-sm">0 chevaux · Box</p>
          <div class="flex items-center mt-2">
            <span class="font-semibold">{{ locationDetails.host }}</span>
            <span class="ml-2 text-gray-600">⭐ {{ locationDetails.rating }}</span>
          </div>

          <!-- Description -->
          <p class="mt-4 text-gray-700">{{ locationDetails.description }}</p>
          <a href="#" class="text-blue-500 mt-2 inline-block">En savoir plus</a>

          <!-- Services proposés -->
          <h2 class="mt-6 text-lg font-semibold">Ce que propose ce box</h2>
          <ul class="mt-2">
            <li v-for="(item, index) in locationDetails.amenities" :key="index" class="flex items-center">
              🔘 <span class="ml-2">{{ item }}</span>
            </li>
          </ul>
        </div>

        <!-- Réservation -->
        <div class="w-full md:w-1/3 bg-white p-6 rounded-lg shadow-lg">
          <p class="text-2xl font-semibold">{{ locationDetails.pricePerNight }} <span class="text-sm text-gray-500">par nuit</span></p>
          
          <div class="mt-4">
            <label class="block text-gray-700 font-semibold">Arrivée</label>
            <input type="date" class="w-full border p-2 rounded-lg mt-1">
          </div>
          <div class="mt-4">
            <label class="block text-gray-700 font-semibold">Départ</label>
            <input type="date" class="w-full border p-2 rounded-lg mt-1">
          </div>
          <div class="mt-4">
            <label class="block text-gray-700 font-semibold">Chevaux</label>
            <select class="w-full border p-2 rounded-lg mt-1">
              <option>1 cheval</option>
              <option>2 chevaux</option>
              <option>3 chevaux</option>
            </select>
          </div>

          <button class="w-full bg-black text-white py-2 mt-6 rounded-lg">Réserver</button>

          <!-- Détails prix -->
          <div class="mt-4 text-gray-700 text-sm">
            <p class="flex justify-between"><span>{{ locationDetails.pricePerNight }} × 0 nuits</span> <span>0€</span></p>
            <p class="flex justify-between"><span>Frais de service</span> <span>0€</span></p>
            <p class="flex justify-between"><span>Taxes</span> <span>0€</span></p>
            <p class="flex justify-between font-bold"><span>Total</span> <span>0€</span></p>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

