<template>
  <div>
    <h1 class="bookname">{{ book.name }}</h1>
    <h2>{{ book.genre }}</h2>
    <h2>{{ book.rating }}</h2>
    <button @click="storingbook">Borrow Book</button>
  </div>
</template>

<script setup>
defineProps({
  book: {
    type: Object,
    required: true,
  },
})
function storingbook() {
  console.log(book.name)
}
</script>

<style scoped></style>
