# Vue Reactivity Project Feedback
**Student:** Andy Zhang

This is a library book borrowing app. The reactive borrowing list works correctly, but the static book catalogue and some component structure issues need attention.

## Vite CLI – Mastery
`package.json` correctly lists `vite` as a dev dependency with `vue-router` and `vue` properly included. The `dev`, `build`, and `preview` scripts are all set up correctly.

## Iteration in Vue – Approaching
`v-for` is used to render both `<bookCard>` and `<BorrowingBook>` components. However, `:key` is bound to `book.name` on both loops — this works only as long as book names are unique. If two books shared a name, Vue would have key collisions. A better approach is to add an `id` field to each book object and use that as the key.

```js
// Add an id to each book:
{ id: 1, name: "To Kill a Mockingbird", ... }
// Then in the template:
<bookCard v-for="book in books" :key="book.id" :book="book">
```

## Data Binding – Approaching
`bookstobeborrowed` is correctly wrapped in `ref([])` and `.value` is used when mutating it in the script. However, **`books` (the main catalogue) is a plain `const` array — not wrapped in `ref`**. For a static list that never changes this technically works for display, but it is not reactive. If you ever wanted to add or remove books from the catalogue, the UI would not update.

```js
// Current (not reactive — won't update if modified):
const books = [...]

// Fix — wrap in ref() for consistency and future-proofing:
import { ref } from 'vue'
const books = ref([...])
```

## Click Methods – Mastery
`@click="storingbook(book)"` is defined on the Borrow button and the `storingbook` function correctly pushes to `bookstobeborrowed.value`. This is the correct pattern.

## Reactive UI – Approaching
Adding a book to the borrowed list via the Borrow button correctly updates the `<BorrowingBook>` list at the top because `bookstobeborrowed` is reactive. However, there is no way to remove a book from the borrowed list — the "Finish Selecting Books" button has no `@click` handler and does nothing. Add a remove/undo function connected to that button or to each `<BorrowingBook>` card.

## Semantic HTML – Not Yet
There are multiple `<h1>` tags used for non-heading purposes inside `bookCard.vue`:

```html
<!-- bookCard.vue — both Title and Author use <h1>: -->
<h1>Title: {{ book.name }}</h1>
<h1>Author: {{ book.author }}</h1>
```

And the same pattern repeats in `borrowingBook.vue`. A page should have only one `<h1>`. Use `<h2>` for the book title and `<p>` or `<span>` for author, genre, and rating.

```html
<!-- Better: -->
<h2>{{ book.name }}</h2>
<p>Author: {{ book.author }}</p>
<p>Genre: {{ book.genre }}</p>
<p>Rating: {{ book.rating }}</p>
```

## BEM CSS – Not Yet
The component files have no CSS classes at all (styles are empty or absent in `bookCard.vue` and `borrowingBook.vue`). The main view has no BEM class names on the card wrappers. There is no `block__element--modifier` naming in use. Add meaningful class names following BEM to your components.

```html
<!-- Example BEM structure for a book card: -->
<div class="book-card">
  <h2 class="book-card__title">{{ book.name }}</h2>
  <p class="book-card__author">{{ book.author }}</p>
  <button class="book-card__button book-card__button--borrow">Borrow</button>
</div>
```

## Bonus – Aesthetics – Not Yet
The components have empty `<style scoped>` blocks and no visual styling has been applied. The page has no layout, no colors, and no spacing beyond the browser default. Add CSS to make the book cards visually distinct and the borrowed list easy to read.

## Summary of Critical Fixes
1. **Fix the `<h1>` overuse** in `bookCard.vue` and `borrowingBook.vue` — only one `<h1>` per page. Change book title to `<h2>` and use `<p>` tags for author/genre/rating.
2. **Add BEM CSS classes** to all component elements — currently there are no classes at all.
3. **Add a remove function** so users can undo borrowing a book — the "Finish Selecting Books" button currently does nothing.
4. Consider adding an `id` field to books and using it as the `:key` instead of `book.name`.
