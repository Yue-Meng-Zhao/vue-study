<script setup>
import { ref, useTemplateRef, onMounted } from 'vue'
import ChildrenItem from './ChildrenItem.vue'

const list = ref(['Fire', 'Air', 'Water'])

const itemRefs = useTemplateRef('items')
const childRef = useTemplateRef('child')


onMounted(() => console.log('childRef', childRef.value.b))
</script>

<template>
  <ul>
    <li
      v-for="(item,index) in list"
      :key="index"
      ref="items">
      {{ item }}
    </li>
  </ul>
  <ChildrenItem ref="child" />
</template>
