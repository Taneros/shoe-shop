<script setup>
import CartItemList from './CartItemList.vue';
import DrawerHead from './DrawerHead.vue';


</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="flex flex-col bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />

    <div class="flex-1 overflow-auto mb-4 pr-2">
      <CartItemList />
    </div>


    <div class="flex flex-col gap-6">

      <div class="flex flex-col gap-4">
        <div class="flex gap-4">
          <span>Итого: </span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>21 498 руб.</b>
        </div>

        <div class="flex gap-4">
          <span>Налог 5%: </span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>1074 руб.</b>
        </div>
      </div>

      <button
              class="bg-lime-400 w-full rounded-xl py-3 text-white hover:bg-lime-500 transition active:bg-lime-600 disabled:bg-slate-300 disabled:cursor-not-allowed	-">Оформить
        заказ</button>

    </div>

  </div>
</template>