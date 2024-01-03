<script setup>
import Props from './components/Props.vue'

</script>

<template>
  <Props title="Title" subtitle="Subtitle" :number="123" :boolean="false"/>
  <Props title="With slot">
    <p>Put in the slot</p>
  </Props>

</template>

<style scoped>

</style>
