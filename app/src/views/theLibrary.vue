<template>
  <div>
    <bookCard v-for="book in books" :key="book.name" :book="book">
      {{ book.name }}
    </bookCard>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import BookCard from '@/components/BookCard.vue'
const books = ref([
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
  { name: '', genre: '', rating: '' },
])
</script>

<style scoped></style>
