<template>
  <div>
    <h1 class="bookname">{{ book.name }}</h1>
    <h2>{{ book.genre }}</h2>
    <h2>{{ book.rating }}</h2>
    <button @click="storingbook(book)">Borrow Book</button>
  </div>
</template>

<script setup>
// import { store } from './store.js'
defineProps({
  book: {
    type: Object,
    required: true,
  },
})
function storingbook(book) {
  console.log(book.name)
  // store.bookstobeborrowed.push(book.name)
}
</script>

<style scoped></style>
