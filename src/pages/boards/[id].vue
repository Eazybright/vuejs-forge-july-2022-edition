<script setup>

import { ref } from 'vue'

const board = ref({
  id: boardId.value,
  title: ''
})
</script>

<template>
  <AppPageHeading>{{ board.title }}</AppPageHeading>
  
</template>