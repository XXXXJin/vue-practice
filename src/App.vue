<script setup>
import NavBar from '@/components/NavBar.vue'
import PageView from './components/PageView.vue'
import { ref } from 'vue'

const pages = ref([
  { text: 'Home', url: 'home.html' },
  { text: 'About', url: 'home.html' },
  { text: 'Services', url: 'home.html' },
  { text: 'Pricing', url: 'home.html' },
  { text: 'Contact', url: 'home.html' }
])
const pageIndex = ref(0)

const changePageIndex = (index) => {
  console.log(index)
  pageIndex.value = index
}
console.log(pageIndex.value)
</script>

<template>
  <NavBar
    v-bind:pages="pages"
    v-bind:pageIndex="pageIndex"
    v-bind:changePageIndex="changePageIndex"
  />
  <PageView />
  <h1>Hello world!!!</h1>
</template>
