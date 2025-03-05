<template>
    <div class='container mx-auto p-4'>

      <h1 class='text-xl font-bold'>Votre Réservation</h1>
      <form>
        <Input label='Nom' />
        <Input label='Email' type='email' />
        <Input label='Date de réservation' type='date' />
        <Button label='Réserver' />
      </form>

    </div>
  </template>
  <script setup>
    import Input from '@/components/Input.vue';
    import Button from '@/components/Button.vue';
  </script>