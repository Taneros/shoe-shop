
<script setup>
import Card from './Card.vue'

defineProps( {
  items: Array,
  favorites: Array,
  addFavorite: Function
} )

const onClickAdd = () => {
  alert( 'Added!' )
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
          v-for="item in items"
          :key="item.id"
          :title="item.title"
          :image-url="item.imageUrl"
          :price="item.price"
          :is-added="true"
          :is-favorite="favorites.some((favorite) => favorite.parentId === item.id)"
          :addFavorite="addFavorite.bind(null, item.id)"
          :onClickAdd="onClickAdd" />
  </div>
</template>