<script setup>
import CartItem from './CartItem.vue';


</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <div class="flex gap-5 items-center">
      <img src="/arrow-next-black.svg" alt="Close Basket"
           class="stroke-black opacity-30 rotate-180 hover:opacity-100 cursor-pointer transition hover:-translate-x-2">
      <h2 class="text-2xl font-bold">Корзина</h2>
    </div>
    <div>
      <CartItem />
    </div>
  </div>
</template>