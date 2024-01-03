<script setup>

defineProps( {
  title: String,
  subtitle: String,
  number: Number,
  boolean: Boolean
})

</script>

<template>
  <h1> {{ title }}</h1>
  <p> {{ subtitle }}</p>
  <p>{{ number }}</p>
  <p>{{ boolean }}</p>
  <slot />
</template>