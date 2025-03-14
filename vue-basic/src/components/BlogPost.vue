<!-- BlogPost.vue -->
<script setup>
defineProps(['title'])
// defineEmits(['enlarge-text'])
const emit = defineEmits(['enlarge-text'])
emit('enlarge-text')

</script>

<template>
  <h4>{{ title }}</h4>
  <button @click="$emit('enlarge-text')">Enlarge text</button>
</template>
