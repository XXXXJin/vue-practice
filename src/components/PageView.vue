<script>
// import { ref } from 'vue'
// const textContent = ref('hi')

export default {
  name: 'App',
  data() {
    return {
      formValue: {
        name: '',
        location: ''
      }
    }
  },
  methods: {
    changeName() {
      this.name = 'bat man'
    },
    handleSubmit() {
      console.log(this.formValue)
    }
  }
}
</script>
<template>
  <p>{{ JSON.stringify(formValue, null, 2) }}</p>
  <form v-on:submit.prevent="handleSubmit">
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" class="border" v-model="formValue.name" />
    </div>
    <div>
      <select name="location" id="location" v-model="formValue.location">
        <option value="">select the location</option>
        <option value="tokyo">tokyo</option>
        <option value="london">london</option>
        <option value="new york">new york</option>
      </select>
    </div>
    <button>submit</button>
  </form>
</template>
