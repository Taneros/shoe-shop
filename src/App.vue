<script setup>
import {onMounted, ref, watch} from 'vue';

import CardList from './components/CardList.vue';
// import Drawer from './components/Drawer.vue';
import Header from './components/Header.vue'
import SearchFilter from './components/SearchFilter.vue';

//TODO 
/**
  * refactor to services
  **/

const responseData = ref( [] )

const urlGetAll = 'https://604781a0efa572c1.mokky.dev/items'

const options = {}

const fetchData = async ( url ) => {
  try {
    const response = await fetch( url, options )

    const data = await response.json()

    console.log( `src/App.vue App.vue - line: 21 ->> data`, data )

    responseData.value = data

    console.log( `src/App.vue App.vue - line: 23 ->> responseData.value`, responseData.value )
  } catch ( error ) {
    console.error( 'Error fetching data', error )
  }
}

onMounted( () => {
  fetchData( urlGetAll )
} )

const sortBy = ref( '' )
const searchQuery = ref( '' )

const sortByUrl = 'https://604781a0efa572c1.mokky.dev/items?sortBy='
const searchUrl = 'https://604781a0efa572c1.mokky.dev/items?title='

watch( sortBy, async () => {
  fetchData( sortByUrl + sortBy.value )
} )

watch( searchQuery, async () => {
  fetchData( sortByUrl + sortBy.value + '?title=' + `*${ searchQuery.value }*` )
} )

const onChangeSelect = event => {
  sortBy.value = event.target.value
}

const onChangeSearch = ( event ) => {
  searchQuery.value = event.target.value
}

</script>

<template>
  <!-- <Drawer /> -->

  <div class="w-4/5 mx-auto bg-white min-h-full rounded-xl shadow-xl">
    <Header />

    <div class="p-10">
      <SearchFilter :onChangeSelect="onChangeSelect" :onChangeSearch="onChangeSearch" />

      <CardList :items="responseData" />

    </div>
  </div>
</template>