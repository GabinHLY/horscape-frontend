<template>
  <div class="container mx-auto p-4 px-30">
    <!-- Galerie d'images -->
    <div class="p-4">
      <!-- Grille principale -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      
      <!-- Image principale (Grande image à gauche) -->
      <div class="md:col-span-2">
        <img src="https://picsum.photos/800/500" alt="Box Image" class="w-full h-72 md:h-[400px] object-cover rounded-lg" />
      </div>
    
      <!-- Galerie d'images (4 petites en 2x2 à droite) -->
      <div class="grid grid-cols-2 gap-2">
        <img src="https://picsum.photos/300/200" alt="Box Image" class="w-full h-full object-cover rounded-lg" />
            <img src="https://picsum.photos/300/200" alt="Box Image" class="w-full h-full object-cover rounded-lg" />
            <img src="https://picsum.photos/300/200" alt="Box Image" class="w-full h-full object-cover rounded-lg" />
            <div class="relative">
            <img src="https://picsum.photos/300/200" alt="Box Image" class="w-full h-full object-cover rounded-lg" />
            <button class="absolute bottom-2 right-2 bg-white px-3 py-1 text-sm rounded-lg shadow-md">
              Afficher toutes les photos
            </button>
          </div>
        </div>
      </div>
    
      <!-- Informations de l'annonce -->
      <div class="mt-4 flex justify-between items-center">
        <div>
          <h2 class="text-lg md:text-xl font-bold">Nom du location de box</h2>
          <p class="text-sm text-gray-600">0 chevaux • 0 box</p>
        </div>
        <div>
          <button class="px-4 py-2 text-sm">Signaler</button>
          <button class="px-4 py-2 text-sm">Enregistrer</button>
          <button class="px-4 py-2 text-sm">Partager</button>
        </div>
      </div>
    </div>
    
    
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-6">
      <!-- Informations du box -->
      <div class="col-span-2">
          <h1 class="text-3xl font-bold">Nom du box</h1>
          <div class="flex items-center mt-3">
              <img src="https://picsum.photos/50/50" alt="Hôte" class="w-12 h-12 rounded-full shadow-md" />
              <div class="ml-3">
                  <p class="text-lg font-semibold">Nom de l'hôte</p>
                  <p class="text-sm text-gray-500 flex items-center">
                      ⭐ <span class="ml-1 font-medium">4.5/5</span>
                  </p>
              </div>
          </div>
          <p class="text-gray-600 text-md my-5 leading-relaxed">
              Explication détaillée du box, ses caractéristiques, et autres détails importants.
              <a href="#" class="text-blue-600 font-medium hover:underline">En savoir plus</a>
          </p>
  
          <!-- Liste des équipements -->
          <div class="my-6">
              <h3 class="text-xl font-semibold mb-3">Ce que propose ce box</h3>
              <ul class="grid grid-cols-2 gap-3">
                  <li class="flex items-center"><span class="text-blue-500 text-lg">●</span> <span class="ml-2">Écurie</span></li>
                  <li class="flex items-center"><span class="text-blue-500 text-lg">●</span> <span class="ml-2">Douche</span></li>
                  <li class="flex items-center"><span class="text-blue-500 text-lg">●</span> <span class="ml-2">Paddock</span></li>
                  <li class="flex items-center"><span class="text-blue-500 text-lg">●</span> <span class="ml-2">Sellerie</span></li>
              </ul>
          </div>
      </div>
  
      <!-- Formulaire de réservation -->
      <div class="border p-5 rounded-lg shadow-lg bg-white">
          <h3 class="text-2xl font-bold">00€ <span class="text-lg font-normal">par nuit</span></h3>
          <div class="mt-5">
              <label class="block text-sm font-bold mb-1">Arrivée</label>
              <input type="date" class="border p-2 w-full rounded-lg focus:ring-2 focus:ring-blue-400 transition" />
  
              <label class="block text-sm font-bold mt-3 mb-1">Départ</label>
              <input type="date" class="border p-2 w-full rounded-lg focus:ring-2 focus:ring-blue-400 transition" />
          </div>
  
          <div class="mt-5">
              <label class="block text-sm font-bold mb-1">Chevaux</label>
              <select class="border p-2 w-full rounded-lg focus:ring-2 focus:ring-blue-400 transition">
                  <option>1 cheval</option>
                  <option>2 chevaux</option>
                  <option>3 chevaux</option>
              </select>
          </div>
  
          <button class="mt-5 bg-blue-600 hover:bg-blue-700 text-white font-semibold p-3 w-full rounded-lg transition">
              Réserver
          </button>
  
          <div class="mt-5 text-sm text-gray-600">
              <p>Frais de service : <span class="font-semibold">00€</span></p>
              <p>Taxes : <span class="font-semibold">00€</span></p>
              <p class="font-bold text-lg mt-2">Total : 00€</p>
          </div>
      </div>
  </div>
    
    
    <!-- Sélection des dates -->
    <div class="my-6">
      <Calendar />
    </div>
    
    <!-- Sélection des box disponibles -->
    <div class="my-6">
      <h3 class="text-lg font-bold">Sélectionner un box</h3>
      <div class="grid grid-cols-6 gap-2">
        <button class="border p-4 rounded-lg">1</button>
        <button class="border p-4 rounded-lg">2</button>
        <button class="border p-4 rounded-lg">3</button>
        <button class="border p-4 rounded-lg">4</button>
        <button class="border p-4 rounded-lg">5</button>
        <button class="border p-4 rounded-lg">6</button>
      </div>
    </div>
    
    <!-- Commentaires et avis -->
    <div class="my-6">
      <h3 class="text-lg font-bold">Avis des utilisateurs</h3>
      <div class="border p-4 rounded-lg">
        <p class="text-gray-600">0,00 • 0 commentaires</p>
      </div>
    </div>
    
    <!-- Localisation -->
    <div class="my-6">
      <h3 class="text-lg font-bold">Où se situe la location</h3>
      <Map />
    </div>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router';
import Rating from '@/components/Rating.vue';
import Calendar from '@/components/Calendar.vue';
import Map from '@/components/Map.vue';

const route = useRoute();
</script>
