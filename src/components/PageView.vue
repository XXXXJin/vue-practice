<script>
// import { ref } from 'vue'
// const textContent = ref('hi')

export default {
  name: 'App',
  data() {
    return {
      textContent: 'hi there',
      style: {
        color: 'red',
        fontSize: '30px',
        num: 3
      },
      names: ['Bruce', 'clark', 'diana'],
      name: 'jin'
    }
  },
  methods: {
    changeName() {
      this.name = 'bat man'
    }
  }
}
</script>
<template>
  <!-- <h1 v-bind:style="{ color: 'blue', ...style, color: 'green' }">{{ textContent }}</h1>
  <p v-if="style.color === 'red'">the color is indeed red</p>
  <p v-else>the color is not red</p> -->
  <!-- <p v-for="name in names" v-bind:key="name">{{ name }}</p> -->
  <p>{{ name }}</p>
  <button v-on:click="changeName">change name</button>
</template>
