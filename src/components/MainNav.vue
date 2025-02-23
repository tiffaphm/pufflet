<script setup>
import Menubar from 'primevue/menubar'
import { ref } from 'vue'

const menuItems = ref([{ label: 'Recipes' }, { label: 'Generator' }, { label: 'Groceries' }])
</script>

<template>
  <Menubar :model="menuItems">
    <template #start>
      <h1>pufflet.</h1>
    </template>
    <template #item="{ item }">
      <span class="text-sm">{{ item.label }}</span>
    </template>
  </Menubar>
</template>

<style scoped>
h1 {
  margin-right: 36px;
  font-weight: bold;
}

span {
  padding: 0 12px;
}
</style>
