<template>
  <div>
    <img :src="book.img" alt="" />
    <h2>Title: {{ book.name }}</h2>
    <p>Author: {{ book.author }}</p>
    <p>Genre: {{ book.genre }}</p>
    <p>Goodreads Rating: {{ book.rating }}</p>
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

<style scoped>
div {
  width: 20%;
}
</style>
