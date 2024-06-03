<template>
  <SiteNatigation />
  <!-- <SearchInput v-on:add-location="addLocation" /> -->
  <RouterView v-on:add-location="addLocation" />
</template>

<script setup>
import SiteNatigation from '@/components/SiteNavigation.vue'
// import SearchInput from '@/components/SearchInput.vue'
import {ref} from 'vue'

const locations = ref([])

const addLocation = (location) => {
  locations.value.push(location)
  console.log(location.value, 123)
}

</script>