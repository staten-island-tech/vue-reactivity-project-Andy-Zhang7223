<template>
  <div>
    <BorrowingBook v-for="book in bookstobeborrowed" :key="book.name" :book="book" />
    <button>Finish Selecting Books</button>
  </div>
  <div>
    <bookCard v-for="book in books" :key="book.name" :book="book">
      <button @click="storingbook(book)">Borrow This Book</button>
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
let bookstobeborrowed = ref([])
function storingbook(book) {
  console.log(book.name)
  bookstobeborrowed.value.push(book.name)
}
</script>

<style scoped></style>
