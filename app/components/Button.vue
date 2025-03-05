<template>
    <button class='bg-blue-500 text-white p-2 rounded'>{{ label }}</button>
  </template>
  <script setup>
    defineProps({ label: String });
  </script>