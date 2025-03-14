<script setup>
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import Test from './components/TestItem.vue'
import TemplateReference from './components/TemplateReference.vue'
import BlogPost from './components/BlogPost.vue';
import AlertBox from './components/AlertBox.vue';
const elements = ["Fire", "Air", "Water"];

console.log(elements.join(""));
const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])
const postFontSize = ref(1)
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <Test />
      <TemplateReference />
      <div :style="{ fontSize: postFontSize + 'em' }">
        <BlogPost
          v-for="post in posts"
          :key="post.id"
          :title="post.title"
          @enlarge-text="postFontSize += 0.1" />
      </div>
      <AlertBox> Something bad happened. </AlertBox>
    </div>
  </header>

  <main></main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
