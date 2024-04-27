<script setup lang="ts">
defineProps<{ msg: string }>()
</script>

<template>
  <h1>{{ msg }}</h1>
  <arco-button type="primary">Primary</arco-button>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
