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

const favoriteList = ref( [] )

const fetchFavoriteList = async () => {
  try {
    let url = 'https://ed1de7919bc7a5d8.mokky.dev/favorites'

    const response = await fetch( url )

    const data = await response.json()

    favoriteList.value = data

  } catch ( error ) {
    console.error( 'Error fetching data', error )
  }
}


const itemList = ref( [] )

const filters = reactive( {
  sortBy: '',
  searchQuery: ''
} )

const fetchItemList = async () => {
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

    itemList.value = data

    console.log( `src/App.vue App.vue - line: 23 ->> responseData.value`, itemList.value )
  } catch ( error ) {
    console.error( 'Error fetching data', error )
  }
}

onMounted( () => {
  fetchItemList()
  fetchFavoriteList()
} )

watch( filters, fetchItemList )

const onChangeSelect = event => {
  filters.sortBy = event.target.value
}

const onChangeSearch = ( event ) => {
  filters.searchQuery = event.target.value
}

const addFavorite = async ( id ) => {
  console.log( `src/App.vue App.vue - line: 81 ->> addFavorite`, id )

  const favoriteItem = favoriteList.value.find( ( favorite ) => favorite.parentId === id )

  if ( !favoriteItem ) {
    favoriteList.value.push( {parentId: id} )
  }

  if ( favoriteItem ) {
    favoriteList.value.splice( favoriteList.value.findIndex( ( item ) => item.parentId === id ), 1 )
  }
}

</script>

<template>
  <!-- <Drawer /> -->

  <div class="w-4/5 mx-auto bg-white min-h-full rounded-xl shadow-xl">
    <Header />

    <div class="p-10">
      <SearchFilter :onChangeSelect="onChangeSelect" :onChangeSearch="onChangeSearch" />

      <CardList :items="itemList" :favorites="favoriteList" :addFavorite="addFavorite" />

    </div>
  </div>
</template>