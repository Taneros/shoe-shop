<script setup>
import {onMounted, ref} from 'vue';

import CardList from './components/CardList.vue';
// import Drawer from './components/Drawer.vue';
import Header from './components/Header.vue'
import SearchFilter from './components/SearchFilter.vue';

const responseData = ref( [] )

const url = 'https://604781a0efa572c1.mokky.dev/items'

const options = {}

const fetchData = async () => {
  try {
    const response = await fetch( url, options )

    const data = await response.json()

    console.log( `src/App.vue App.vue - line: 21 ->> data`, data )

    responseData.value = data.slice( 0, 12 )

    console.log( `src/App.vue App.vue - line: 23 ->> responseData.value`, responseData.value )
  } catch ( error ) {
    console.error( 'Error fetching data', error )
  }
}

onMounted( () => {
  fetchData()
} )

</script>

<template>
  <!-- <Drawer /> -->

  <div class="w-4/5 mx-auto bg-white min-h-full rounded-xl shadow-xl">
    <Header />

    <div class="p-10">
      <SearchFilter />

      <CardList :items="responseData" />

    </div>
  </div>
</template>