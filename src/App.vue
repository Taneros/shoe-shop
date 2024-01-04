<script setup>
import CardList from './components/CardList.vue';
import Header from './components/Header.vue'
</script>

<template>
  <div class="w-4/5 mx-auto bg-white min-h-full rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

      <CardList />
    </div>
  </div>
</template>

<style scoped></style>
