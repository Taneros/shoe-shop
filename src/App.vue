<script setup>
import {onMounted, reactive, ref, watch} from 'vue';

import CardList from './components/CardList.vue';
// import Drawer from './components/Drawer.vue';
import Header from './components/Header.vue'
import SearchFilter from './components/SearchFilter.vue';

//TODO 
/**
  * refactor to services
  **/

const responseData = ref( [] )

const filters = reactive( {
  sortBy: '',
  searchQuery: ''
} )

const fetchData = async () => {
  try {
    let url = 'https://604781a0efa572c1.mokky.dev/items'

    if ( filters.sortBy !== '' ) {
      url += `?sortBy=${ filters.sortBy }`;
    }

    if ( filters.searchQuery !== '' ) {
      url += `${ filters.sortBy !== '' ? '&' : '?' }title=*${ filters.searchQuery }*`;
    }

    const response = await fetch( url )

    const data = await response.json()

    console.log( `src/App.vue App.vue - line: 21 ->> data`, data )

    responseData.value = data

    console.log( `src/App.vue App.vue - line: 23 ->> responseData.value`, responseData.value )
  } catch ( error ) {
    console.error( 'Error fetching data', error )
  }
}

onMounted( () => {
  fetchData()
} )

watch( filters, fetchData )

const onChangeSelect = event => {
  filters.sortBy = event.target.value
}

const onChangeSearch = ( event ) => {
  filters.searchQuery = event.target.value
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