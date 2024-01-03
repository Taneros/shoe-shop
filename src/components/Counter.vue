// composition API
<script setup>
import { ref } from 'vue'

let count = ref(0) // reactive approach?

function increment() {
  count.value += 1
}

function updateCount(event) {
  count.value = Number(event.target.value)
}

</script>

// options API
<!-- <script>
export default {
//state
  data () {
    return {
        count: 0
      }
  },
  methods: {
    increment () {
        this.count += 1
      }
    }
  }
</script> -->

<template>
  <h2>{{ count }}</h2>
  <input @input="updateCount">
  <button @click="increment">increment() +</button>
  <button @click="count++">Directly count++</button>
  <!-- <input v-on:input="updateCount"> -->
  <!-- <input v-model="count"> -->
</template>
