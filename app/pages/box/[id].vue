<template>
  <div class="p-4">
    <!-- Galerie d'images -->
    <div class="grid grid-cols-2 gap-2 md:grid-cols-3">
      <div class="col-span-2 md:col-span-2">
        <img
          :src="images[0]"
          alt="Box Image"
          class="w-full h-64 sm:h-80 md:h-[400px] object-cover rounded-lg cursor-pointer"
          @click="showLightbox(0)"
        />
      </div>
      <div class="grid grid-cols-2 gap-2">
        <img
          v-for="(img, i) in images.slice(1, 4)"
          :key="i"
          :src="img"
          class="w-full h-full object-cover rounded-lg cursor-pointer"
          @click="showLightbox(i + 1)"
        />
        <div class="relative">
          <img
            :src="images[4]"
            alt="Box Image"
            class="w-full h-full object-cover rounded-lg cursor-pointer"
            @click="showLightbox(4)"
          />
          <button
            class="absolute bottom-2 right-2 bg-white px-3 py-1 text-sm rounded-lg shadow-md"
            @click="showLightbox(0)"
          >
            Afficher toutes les photos
          </button>
        </div>
      </div>
    </div>

    <vue-easy-lightbox
      :visible="lightboxVisible"
      :imgs="images"
      :index="lightboxIndex"
      @hide="lightboxVisible = false"
    />

    <!-- Description + Réservation -->
    <div class="grid md:grid-cols-3 gap-8 mt-10 py-6">
      <!-- Description -->
      <div class="md:col-span-2 space-y-6">
      <h1 class="text-3xl font-semibold text-gray-900">{{ box?.name }}</h1>
      <p class="text-sm text-gray-600">{{ box?.chevaux || 0 }} chevaux • {{ box?.boxes || 0 }} box</p>

      <div class="flex items-center mt-6 gap-3 border-b pb-6">
        <img src="/images/profil.svg" alt="avatar" class="w-12 h-12 rounded-full bg-gray-200" />
        <div>
        <p class="text-sm font-medium text-gray-800">Nom de l'hôte</p>
        <p class="text-sm font-medium text-gray-800 flex"><span class="flex items-center text-xs text-gray-500"><img src="/images/star.svg" alt="Star Rating" class="h-3 mr-1 -mt-1"> 0,00</span></p>
        </div>
      </div>

      <p class="mt-6 mb-4 text-sm text-gray-700 leading-relaxed min-h-[100px]">
        <span class="font-semibold">Description de la location : </span>
        {{ showMore ? box?.description : box?.description?.slice(0, 300) + '...' }}
      </p>
      <button
        class="text-sm my-4 underline text-gray-600"
        @click="showMore = !showMore"
      >
        {{ showMore ? 'Réduire' : 'En savoir plus' }}
      </button>

      <p class="mt-6 text-sm text-gray-700">
        <span class="font-semibold">Adresse : </span>{{ box?.adress }}
      </p>

      <div class="mt-8 mb-6">
        <h2 class="font-semibold mb-4 text-gray-900 text-lg">Ce que propose ce box</h2>
        <ul class="grid grid-cols-2 gap-6 text-sm text-gray-700">
          <li v-for="(item, i) in boxFeatures" :key="i" class="flex items-center gap-2 py-2">
            <div class="w-2.5 h-2.5 bg-black rounded-full"></div>
            {{ item }}
          </li>

        </ul>
      </div>
      </div>

      <!-- Réservation -->
      <div class="min-h-[600px] flex items-start">
      <div class="rounded-xl border-shadow bg-white p-8 shadow-2xl hover:shadow-2xl transition-shadow text-sm space-y-8 w-full sticky top-10" style="box-shadow: 0 20px 35px -5px rgba(0, 0, 0, 0.3), 0 12px 15px -6px rgba(0, 0, 0, 0.2);">
        <!-- Prix -->
        <p class="text-2xl font-semibold text-gray-900">
        {{ box?.price }}€ <span class="text-sm font-normal text-gray-600">par nuit</span>
        </p>

        <!-- Dates + Select -->
        <div class="border border-gray-300 rounded-lg overflow-hidden divide-y divide-gray-300">
        <div class="grid grid-cols-2 divide-x divide-gray-300">
          <div class="p-4">
          <label class="text-xs text-gray-500">Arrivée</label>
          <input type="date" v-model="startDate" class="w-full border-none focus:outline-none text-sm py-2" />
          </div>
          <div class="p-4">
          <label class="text-xs text-gray-500">Départ</label>
          <input type="date" v-model="endDate" class="w-full border-none focus:outline-none text-sm py-2" />
          </div>
        </div>
        <div class="p-4">
          <label class="text-xs text-gray-500">Chevaux</label>
          <select class="w-full border-none focus:outline-none text-sm py-2">
          <option>1 cheval</option>
          <option>2 chevaux</option>
          </select>
        </div>
        </div>

        <!-- Bouton -->
        <button class="w-full bg-gradient-to-r from-[#0F5B55] to-[#1DA096] text-white font-semibold py-4 rounded-md text-base hover:opacity-90 transition-opacity">
        Réserver
        </button>

        <!-- Détails du prix -->
        <div class="text-gray-700 space-y-4 text-sm pt-4">
        <div class="flex justify-between underline py-1">
          <p>{{ box?.price }}€ x {{ nights }} nuits</p>
          <p>{{ total }}€</p>
        </div>
        <div class="flex justify-between underline py-1">
          <p>Frais de service</p>
          <p>0€</p>
        </div>
        <div class="flex justify-between underline py-1">
          <p>Taxes</p>
          <p>0€</p>
        </div>
        <hr class="my-2" />
        <div class="flex justify-between font-semibold text-base py-2">
          <p>Total</p>
          <p>{{ total }}€</p>
        </div>
        </div>
      </div>
      </div>

    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import VueEasyLightbox from 'vue-easy-lightbox';

const route = useRoute();
const box = ref<any>(null);
const showMore = ref(false);

const fetchBox = async () => {
  const { data } = await useFetch(
    () => `${useRuntimeConfig().public.NUXT_PUBLIC_API_BASE}/boxes/${route.params.id}`
  );
  box.value = data.value;
};

onMounted(fetchBox);

const images = [
  '/images/details/1.jpg',
  '/images/details/2.jpg',
  '/images/details/3.jpg',
  '/images/details/4.jpg',
  '/images/details/5.jpg',
];

const lightboxVisible = ref(false);
const lightboxIndex = ref(0);

const showLightbox = (index: number) => {
  lightboxIndex.value = index;
  lightboxVisible.value = true;
};

const startDate = ref('');
const endDate = ref('');

const nights = computed(() => {
  if (!startDate.value || !endDate.value) return 0;
  const start = new Date(startDate.value);
  const end = new Date(endDate.value);
  const diff = (end.getTime() - start.getTime()) / (1000 * 60 * 60 * 24);
  return diff > 0 ? diff : 0;
});

const total = computed(() => {
  return box.value ? (nights.value * parseFloat(box.value.price)).toFixed(2) : '0.00';
});

const boxFeatures = [
  "Pension en parc individuel",
  "Accès direct à la forêt pour randonnées",
  "Surveillance quotidienne des chevaux",
  "Foin et eau à volonté",
  "Boxes paillés tous les jours",
  "Sellerie sécurisée pour le matériel"
];

</script>

<style scoped>
img:hover {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
</style>
