<template>
  <div>
    <BorrowingBook v-for="book in bookstobeborrowed" :key="book.name" :book="book">
      <button @click="removingbook(book)">Remove This Book</button>
    </BorrowingBook>
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
//Used Chatgpt for the array...
const books = [
  {
    name: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    genre: 'Classic / Historical Fiction',
    rating: 4.26,
  },
  {
    name: '1984',
    author: 'George Orwell',
    genre: 'Dystopian / Science Fiction',
    rating: 4.2,
  },
  {
    name: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    genre: 'Classic / Literary Fiction',
    rating: 3.93,
  },
  {
    name: "Harry Potter and the Sorcerer's Stone",
    author: 'J.K. Rowling',
    genre: 'Fantasy / Young Adult',
    rating: 4.47,
  },
  {
    name: 'The Lord of the Rings',
    author: 'J.R.R. Tolkien',
    genre: 'Epic Fantasy',
    rating: 4.41,
  },
  {
    name: 'The Hunger Games',
    author: 'Suzanne Collins',
    genre: 'Dystopian / Young Adult',
    rating: 4.35,
  },
  {
    name: 'Pride and Prejudice',
    author: 'Jane Austen',
    genre: 'Classic / Romance',
    rating: 4.3,
  },
  {
    name: 'The Book Thief',
    author: 'Markus Zusak',
    genre: 'Historical Fiction / Young Adult',
    rating: 4.39,
  },
  {
    name: 'The Alchemist',
    author: 'Paulo Coelho',
    genre: 'Philosophical Fiction / Adventure',
    rating: 3.9,
  },
  {
    name: 'The Da Vinci Code',
    author: 'Dan Brown',
    genre: 'Mystery / Thriller',
    rating: 3.94,
  },
]
let bookstobeborrowed = ref([])
function storingbook(book) {
  const id = 1
  console.log(book.name)
  bookstobeborrowed.value.push(book)
}
function removingbook(book) {
  bookstobeborrowed.value.splice(book)
}
</script>

<style scoped></style>
