<script setup>
import axios from 'axios';
import {reactive} from 'vue'
const searchTerm = reactive({
  query: '',
  timeout: null,
  result: []
})

const handleSearch = () => {
  clearTimeout(searchTerm.timeout);
  searchTerm.timeout = setTimeout(() => {
    if(searchTerm.query !== '') {
      axios.get(`http://api.weatherapi.com/v1/search.json?key=01310cb2121b4b32ab181800240306&q=${searchTerm.query}`).then(result => {
        searchTerm.result = result.data
        console.log(result.data)
      }).catch((err) => {
        console.log(err)
      });
    } else {
      searchTerm.result = null
    }
  }, 700);
}
</script>

<template>
  <div class="container">
    <form class="mt-6">
      <div class="bg-white border  rounded-lg shadow-lg flex items-center">
        <i class="fa-solid fa-magnifying-glass p-2 "></i>
        <input
          type="text"
          placeholder="Search for a place"
          class="rounded-r-lg p-2 border-0 outline-0 focus:ring-2  ring-inset w-full"
          v-model="searchTerm.query"
          v-on:input="handleSearch"
        />
      </div>
    </form>

    <div class="bg-white my-2 rounded-lg shadow-lg">
      <template v-if="searchTerm && searchTerm.length !== 0">
        <div v-for="location in searchTerm.result" :key="location.id">
          <button class="px-3 my-2 hover:font-bold w-full text-left">{{ `${location.country}, ${location.region}, ${location.name}` }}</button>
        </div>
        </template>
    </div>
  </div>
</template>
