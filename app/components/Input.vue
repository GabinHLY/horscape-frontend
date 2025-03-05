<template>
    <div class='mb-2'>
      <label class='block font-bold'>{{ label }}</label>
      <input :type='type' class='border p-2 w-full rounded' />
    </div>
  </template>
  <script setup>
    defineProps({ label: String, type: { type: String, default: 'text' } });
  </script>