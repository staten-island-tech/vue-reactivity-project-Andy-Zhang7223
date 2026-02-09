<template>
  <div>
    <h1>{{ book.name }}</h1>
    <h2>{{ book.genre }}</h2>
    <h2>{{ book.rating }}</h2>
  </div>
</template>

<script setup>
defineProps({
  book: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped></style>
