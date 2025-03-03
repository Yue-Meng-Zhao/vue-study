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
const awesome = ref(true)
const numbers = ref([1, 2, 3, 4, 5])
const name = ref('Vue.js')
const checked = ref(false)
const checkedNames = ref([])
const selected = ref('')
const picked = ref('')
const toggle = ref('yes')
const pick = ref('second')
const first = ref('first')
const second = ref('second')
const message = ref('Hello Vue!')

const evenNumbers = computed(() => {
  return numbers.value.filter((n) => n%2 == 0)
})

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

function greet(event) {
  alert(`Hello ${name.value}!`)
  // `event` 是 DOM 原生事件
  if (event) {
    alert(event.target.tagName)
  }
}

function warn(message, event) {
  // 这里可以访问原生事件
  if (event) {
    event.preventDefault()
  }
  alert(message)
}

function doSomething() {
  alert('Doing something...')
}

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
  <div>
    <button @click="awesome = !awesome">Toggle</button>

    <h2 v-if="awesome">Vue is awesome!</h2>
    <h2 v-else>Oh no 😢</h2>
    <li v-for="n in evenNumbers" :key="n"> {{n}}</li>
    <button @click="greet">Greet</button>
    <button @click="(event) => warn('Form cannot be submitted yet.', event)">
      Submit
    </button>
    <div @contextmenu.ctrl.prevent="doSomething">Do something</div>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>

    <div>Checked names: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
    <label for="jack">Jack</label>

    <input type="checkbox" id="john" value="John" v-model="checkedNames" />
    <label for="john">John</label>
    
    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
    <label for="mike">Mike</label>

    <div>Selected: {{ selected }}</div>

    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>

    <div>
      <input type="checkbox" v-model="picked" />
      <div>{{ picked }}</div>
    </div>

    <input
      type="checkbox"
      v-model="toggle"
      true-value="yes"
      false-value="no" />
    <div>{{ toggle }}</div>

    <input type="radio" v-model="pick" :value="first" />
    <input type="radio" v-model="pick" :value="second" />

    <input v-model.lazy="message" />
    <div>{{ message }}</div>



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
