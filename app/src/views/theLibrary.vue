<template>
  <div>
    <BorrowingBook v-for="book in bookstobeborrowed" :key="book.id" :book="book">
      <button @click="removingBook(book)" id="0">Remove This Book</button>
    </BorrowingBook>
    <button>Finish Selecting Books</button>
  </div>
  <div>
    <bookCard v-for="book in books" :key="book.name" :book="book">
      <button @click="storingBook(book)">Borrow This Book</button>
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
    id: 1,
    borrowed: false,
    name: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    genre: 'Classic / Historical Fiction',
    rating: 4.26,
  },
  {
    id: 2,
    borrowed: false,
    name: '1984',
    author: 'George Orwell',
    genre: 'Dystopian / Science Fiction',
    rating: 4.2,
  },
  {
    id: 3,
    borrowed: false,
    name: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    genre: 'Classic / Literary Fiction',
    rating: 3.93,
  },
  {
    id: 4,
    borrowed: false,
    name: "Harry Potter and the Sorcerer's Stone",
    author: 'J.K. Rowling',
    genre: 'Fantasy / Young Adult',
    rating: 4.47,
  },
  {
    id: 5,
    borrowed: false,
    name: 'The Lord of the Rings',
    author: 'J.R.R. Tolkien',
    genre: 'Epic Fantasy',
    rating: 4.41,
  },
  {
    id: 6,
    borrowed: false,
    name: 'The Hunger Games',
    author: 'Suzanne Collins',
    genre: 'Dystopian / Young Adult',
    rating: 4.35,
  },
  {
    id: 7,
    borrowed: false,
    name: 'Pride and Prejudice',
    author: 'Jane Austen',
    genre: 'Classic / Romance',
    rating: 4.3,
  },
  {
    id: 8,
    borrowed: false,
    name: 'The Book Thief',
    author: 'Markus Zusak',
    genre: 'Historical Fiction / Young Adult',
    rating: 4.39,
  },
  {
    id: 9,
    borrowed: false,
    name: 'The Alchemist',
    author: 'Paulo Coelho',
    genre: 'Philosophical Fiction / Adventure',
    rating: 3.9,
  },
  {
    id: 10,
    borrowed: false,
    name: 'The Da Vinci Code',
    author: 'Dan Brown',
    genre: 'Mystery / Thriller',
    rating: 3.94,
  },
]
let bookstobeborrowed = ref([])
function storingBook(book) {
  console.log(book.name)
  if (book.borrowed === true) {
    return
  } else {
    bookstobeborrowed.value.push(book)
    book.borrowed = true
  }
}
function removingBook(book) {
  book.borrowed = false
  //Don't use querySelector but maybe something like it?
}
</script>

<style scoped></style>
