<script setup>
import CardList from './components/CardList.vue';
import Drawer from './components/Drawer.vue';
import Header from './components/Header.vue'
import SearchFilter from './components/SearchFilter.vue';


</script>

<template>
  <!-- <Drawer /> -->

  <div class="w-4/5 mx-auto bg-white min-h-full rounded-xl shadow-xl">
    <Header />

    <div class="p-10">
      <SearchFilter />

      <CardList />


    </div>
  </div>
</template>