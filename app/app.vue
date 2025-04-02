<script setup>
import Navbar from '~/components/Navbar.vue';
import Footer from '~/components/Footer.vue';
import { useHead } from '#imports';

useHead({
  title: 'Horscape',
  meta: [
    { name: 'description', content: 'Description de mon site pour le SEO' }
  ]
});
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <Navbar />
    <main class="flex-grow container mx-auto p-4">
      <NuxtPage />
    </main>
    <Footer />
  </div>
</template>
