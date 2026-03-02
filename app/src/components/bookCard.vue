<template>
  <div>
    <h1>Title: {{ book.name }}</h1>
    <h1>Author: {{ book.author }}</h1>
    <h2>Genre: {{ book.genre }}</h2>
    <h2>Goodreads Rating: {{ book.rating }}</h2>
    <slot></slot>
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
