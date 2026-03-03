<template>
  <div>
    <h2>{{ book.name }}</h2>
    <p>{{ book.author }}</p>
    <p>{{ book.genre }}</p>
    <p>{{ book.rating }}</p>
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
