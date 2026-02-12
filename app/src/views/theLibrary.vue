<template>
  <div>
    <BorrowingBook v-for="book in bookstobeborrowed" :key="book.name" :book="book">
      {{ book.name }}
      {{ book.genre }}
      {{ book.rating }}
    </BorrowingBook>
  </div>
  <div>
    <bookCard v-for="book in books" :key="book.name" :book="book">
      {{ book.name }}
      {{ book.genre }}
      {{ book.rating }}
    </bookCard>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import bookCard from '@/components/bookCard.vue'
import BorrowingBook from '@/components/borrowingBook.vue'
const books = ref([{ name: 'Frieren Beyond Journeys End', genre: 'Manga', rating: 10 }])
const bookstobeborrowed = ref([])
</script>

<style scoped></style>
