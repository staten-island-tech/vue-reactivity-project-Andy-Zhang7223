<template>
  <div>
    <form action="submit" @submit.prevent="addnewbook(newbook)">
      <h1>Would you like to add a book?</h1>
      <label for="bookname">Book's Name</label>
      <input type="text" v-model="newbook.bookname" />
      <label for="bookgenre">Book's Genre</label>
      <input type="text" v-model="newbook.bookgenre" />
      <label for="bookrating">Book's Rating</label>
      <input type="text" v-model="newbook.bookrating" />
      <button @click="addnewbook" type="submit">Add New Book</button>
    </form>
  </div>
  <div>
    <bookCard v-for="book in books" :key="book.name" :book="book">
      {{ book.name }}
    </bookCard>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'
import { bookCard } from '@/components/bookCard.vue'
const books = ref([{ name: 'Friren Beyond Journeys End', genre: 'Manga', rating: 'idk' }])
const newbook = reactive({ bookname: '', bookgenre: '', bookrating: '' })
function addnewbook(newbook) {
  console.log(newbook)
}
</script>

<style scoped></style>
