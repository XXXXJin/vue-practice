<script>
import NavBar from '@/components/NavBar.vue'
import PageView from './components/PageView.vue'

export default {
  name: 'App',
  data() {
    return {
      pages: [
        { text: 'Home', url: 'home.html' },
        { text: 'About', url: 'home.html' },
        { text: 'Services', url: 'home.html' },
        { text: 'Pricing', url: 'home.html' },
        { text: 'Contact', url: 'home.html' }
      ],
      pageIndex: 0,
      name: 'jinahixu'
    }
  },
  methods: {
    changePageIndex(index) {
      this.pageIndex = index
    }
  },
  components: {
    NavBar,
    PageView
  },
  provide() {
    return {
      username: this.name
    }
  }
}
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
