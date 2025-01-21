<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import NextuViewHelloWorld from './views/NextuViewHelloWorld.vue'
import ProductsListView from './views/ProductsListView.vue'
</script>

<template>
  <ProductsListView :products="[{ id: 1, label: 'Carotte', description: 'description', quantity: 1 }, { id: 2, label: 'Tomate', description: 'description', quantity: 0 }]" />
</template>
<style scoped>
</style>
