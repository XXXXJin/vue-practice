<script>
// import { ref } from 'vue'
// const textContent = ref('hi')

export default {
  name: 'App',
  data() {
    return {
      formValue: {
        name: ''
      }
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
  <p>{{ formValue.name }}</p>
  <form action="">
    <label for="name">Name</label>
    <input type="text" id="name" v-model="formValue.name" />
  </form>
</template>
