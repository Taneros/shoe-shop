
<script setup>
import Card from './Card.vue'


const onClickAdd = () => {
  alert( 'Added!' )
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card image-url="/sneakers/sneakers-1.jpg" title="Мужские Кроссовки Nike Blazer Mid Suede" :price="12999"
          :is-added="true" :is-favorite="true" :onClickAdd="onClickAdd" />
  </div>
</template>