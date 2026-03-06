<template>
  <div class="borrowingDiv">
    <BorrowingBook
      class="borrowingCards"
      v-for="book in bookstobeborrowed"
      :key="book.id"
      :book="book"
    >
      <button @click="removingBook(book)" id="0">Remove This Book</button>
    </BorrowingBook>
    <button @click="boughtBooks()">Finish Selecting Books</button>
  </div>
  <div class="booksDiv">
    <bookCard class="bookCards" v-for="book in books" :key="book.name" :book="book">
      <button @click="storingBook(book)">Borrow This Book</button>
    </bookCard>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import bookCard from '@/components/bookCard.vue'
import BorrowingBook from '@/components/borrowingBook.vue'
//Used Chatgpt for the array...
//trying to get images to work...
const books = [
  {
    id: 1,
    borrowed: false,
    img: 'https://cdn2.penguin.com.au/covers/original/9780434020485.jpg',
    name: 'To Kill a Mockingbird',
    author: 'Harper Lee',
    genre: 'Classic / Historical Fiction',
    rating: 4.26,
  },
  {
    id: 2,
    borrowed: false,
    img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQogxUXoWEtndRag9TwFDky-3svWQt6QgXP8w&s',
    name: '1984',
    author: 'George Orwell',
    genre: 'Dystopian / Science Fiction',
    rating: 4.2,
  },
  {
    id: 3,
    borrowed: false,
    img: 'https://m.media-amazon.com/images/I/81T4dS6IkaL._AC_UF1000,1000_QL80_.jpg',
    name: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    genre: 'Classic / Literary Fiction',
    rating: 3.93,
  },
  {
    id: 4,
    borrowed: false,
    img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSlwU1Uvtx5Daltv4NJteo0IYEtVBu8NZTumw&s',
    name: "Harry Potter and the Sorcerer's Stone",
    author: 'J.K. Rowling',
    genre: 'Fantasy / Young Adult',
    rating: 4.47,
  },
  {
    id: 5,
    borrowed: false,
    img: 'https://m.media-amazon.com/images/I/81nV6x2ey4L._AC_UF1000,1000_QL80_.jpg',
    name: 'The Lord of the Rings',
    author: 'J.R.R. Tolkien',
    genre: 'Epic Fantasy',
    rating: 4.41,
  },
  {
    id: 6,
    borrowed: false,
    img: 'https://m.media-amazon.com/images/I/61I24wOsn8L._AC_UF1000,1000_QL80_.jpg',
    name: 'The Hunger Games',
    author: 'Suzanne Collins',
    genre: 'Dystopian / Young Adult',
    rating: 4.35,
  },
  {
    id: 7,
    borrowed: false,
    img: 'https://prodimage.images-bn.com/pimages/9780593622452_p0_v1_s600x595.jpg',
    name: 'Pride and Prejudice',
    author: 'Jane Austen',
    genre: 'Classic / Romance',
    rating: 4.3,
  },
  {
    id: 8,
    borrowed: false,
    img: 'https://cdn1.bookmanager.com/i/m?b=3W8tARS3yMxWkONRKgXF_w&cb=1709612196',
    name: 'The Book Thief',
    author: 'Markus Zusak',
    genre: 'Historical Fiction / Young Adult',
    rating: 4.39,
  },
  {
    id: 9,
    borrowed: false,
    img: 'https://m.media-amazon.com/images/I/81ioPZFMeUL._UF1000,1000_QL80_.jpg',
    name: 'The Alchemist',
    author: 'Paulo Coelho',
    genre: 'Philosophical Fiction / Adventure',
    rating: 3.9,
  },
  {
    id: 10,
    borrowed: false,
    img: 'https://m.media-amazon.com/images/I/91FWKxNXR9L._AC_UF1000,1000_QL80_.jpg',
    name: 'The Da Vinci Code',
    author: 'Dan Brown',
    genre: 'Mystery / Thriller',
    rating: 3.94,
  },
]
let bookstobeborrowed = ref([])
function storingBook(book) {
  if (book.borrowed === true) {
    return
  } else {
    bookstobeborrowed.value.push(book)
    book.borrowed = true
  }
}
function removingBook(book) {
  book.borrowed = false
  bookstobeborrowed.value.splice(bookstobeborrowed.value.indexOf(book), 1)
}
function boughtBooks() {
  bookstobeborrowed.value.splice(0, 999)
  books.forEach((book) => (book.borrowed = false))
}
</script>

<style scoped></style>
