<script>
import Hello from '@/components/Hello.vue'
import { ref } from 'vue'

export default {
  name: 'App',
  setup() {
    const formValue = ref({
      name: '321',
      location: '456',
      age: null
    })
    const heros = ref([])
    return {
      formValue,
      heros
    }
  },
  methods: {
    changeName() {
      this.forValue.name = 'bat man'
    },
    handleSubmit() {}
  },
  components: {
    Hello: Hello
  }
}
</script>
<template>
  <p>{{ JSON.stringify(formValue, null, 2) }}</p>
  <p>{{ JSON.stringify(heros, null, 2) }}</p>
  <form v-on:submit.prevent="handleSubmit">
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" class="border" v-model.trim.lazy="formValue.name" />
    </div>
    <div>
      <label for="age">Age</label>
      <input type="number" id="age" v-model.number="formValue.age" class="border" />
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

  <div>
    <button v-on:click="heros.push('wonder women')">add wonder women</button>
  </div>
  <Hello v-bind:name="formValue.name" id="helloConponent" />
</template>
