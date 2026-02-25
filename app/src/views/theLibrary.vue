<template>
  <div>
    <BorrowingBook v-for="book in bookstobeborrowed" :key="book.name" :book="book">
      {{ book.name }}
    </BorrowingBook>
    <button>Finish Selecting Books</button>
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
const books = ref([
  { name: 'Frieren Beyond Journeys End', genre: 'Manga', rating: 10 },
  { name: 'Chainsaw Man', genre: 'Manga', rating: 9 },
])
</script>

<style scoped></style>
