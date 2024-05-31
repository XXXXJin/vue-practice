<script>
import NavBar from '@/components/NavBar.vue'
import PageView from './components/PageView.vue'
import PopUp from '@/components/PopUp.vue'
import SlotComponent from '@/components/SlotComponent.vue'

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
      name: 'jinahixu',
      showPopup: false
    }
  },
  methods: {
    changePageIndex(index) {
      this.pageIndex = index
    },
    closePopup(secret) {
      if (secret === 'secret') this.showPopup = false
    }
  },
  components: {
    NavBar,
    PageView,
    PopUp,
    SlotComponent
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
  <!-- <h1 v-show="showPopup" v-on:closePopup="showPopup = false">Hello world!!!</h1> -->
  <PopUp v-show="showPopup" v-on:closePopup="closePopup"></PopUp>
  <button v-on:click="showPopup = true">show the pop</button>
  <SlotComponent>
    <template v-slot:header>header slot</template>
    <template v-slot:default>default slot</template>
    <template v-slot:footer>footer slot</template>
  </SlotComponent>
</template>
