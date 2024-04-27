<script setup>
import { createDialog } from './components/JsxDialog'
const openDialog = () => {
  const dialog = createDialog({
    text: 'aaa',
    onOk: () => {
      dialog.close()
    }
  })
}
</script>

<template>
  <button @click="openDialog">测试</button>
</template>

<style scoped>
</style>
