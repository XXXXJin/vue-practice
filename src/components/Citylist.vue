<template>
  <div
    v-for="(city, index) in citiesData"
    :key="index"
    class="flex justify-between items-center border border-gray-200 rounded-lg shadow hover:bg-gray-100 p-6 my-3 cursor-pointer"
    @:click="goToCityView(index)"
  >
    <div>
      <p class="text-3xl">{{ city.location.name }}</p>
      <p class="text-sm">
        {{
          new Date(city.location.localtime).getHours() +
          ':' +
          new Date(city.location.localtime).getMinutes()
        }}
      </p>
    </div>
    <div>
      <img :src="city.current.condition.icon" alt="" />
    </div>
    <div class="text-center">
      <p class="text-2xl">{{ Math.round(city.current.temp_c) }}&deg;</p>
      <div class="flex text-sm gap-2">
        <p>最高:{{ Math.round(city.forecast.forecastday[0].day.maxtemp_c) }}&deg;</p>
        <p>最低:{{ Math.round(city.forecast.forecastday[0].day.mintemp_c) }}&deg;</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'
import { useRouter } from 'vue-router'
const savedCities = ref([])
const citiesData = ref([])
const router = useRouter()
const getCities = async () => {
  if (localStorage.getItem('savedCities')) {
    savedCities.value = JSON.parse(localStorage.getItem('savedCities'))
  }
  const requests = []
  savedCities.value.forEach((city) => {
    requests.push(
      axios.get(
        `http://api.weatherapi.com/v1/forecast.json?key=01310cb2121b4b32ab181800240306&q=id:${city}&days=7&aqi=no&alerts=no`
      )
    )
  })
  const weatherData = await Promise.all(requests)
  weatherData.forEach((value, index) => {
    citiesData.value[index] = value.data
  })
}
await getCities()

const goToCityView = (index) => {
  const city = savedCities.value[index]
  router.push({
    name: 'cityView',
    params: { id: city }
  })
}
</script>
