<template>
    <div class='flex items-center'>
      <span v-for='star in 5' :key='star' class='text-yellow-400 text-xl'>&#9733;</span>
      <p class='ml-2'>4.5/5</p>
    </div>
  </template>