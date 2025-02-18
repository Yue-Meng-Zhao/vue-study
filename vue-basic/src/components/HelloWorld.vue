<script setup>
import { computed, reactive, ref } from 'vue'
defineProps({
  msg: {
    type: String,
    required: true,
  },
})

const count = ref(0)
const firstName = ref('John')
const lastName = ref('Doe')

const method = () => {
  fullName.value = 'Allison Harward'
}

const author = reactive({
  name: 'John Doe',
  books: ['Vue 3 Guide', 'Vue 3 Cookbook'],
})

const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})

const fullName = computed( {
  get() {
    return firstName.value + ' ' + lastName.value
  },
  set(newValue) {
    [firstName.value, lastName.value] = newValue.split(' ')

  }
})

</script>

<template>
  <div class="greetings">
    <h1 @click="method" class="green">{{ count }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vite.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span>
    <p>Full Name: {{fullName}}</p>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
