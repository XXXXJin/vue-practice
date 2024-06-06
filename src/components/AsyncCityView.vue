<template>
  <div class="mt-12 mx-32">
    <div class="flex flex-col items-center">
      <h1 class="text-3xl mt-6">{{ location.country }}</h1>
      <p class="mt-3">{{ new Date().toLocaleString() }}</p>
      <p class="text-7xl my-6">{{ current.temp_c }}℃</p>
      <p>体感温度: {{ current.feelslike_c }}</p>
      <img class="w-auto h-30 mt-6" :src="current.condition.icon" alt="" />
    </div>
    <hr class="w-full h-1 mx-auto my-4 bg-gray-200 border-0 rounded md:my-10 dark:bg-gray-700" />
    <h2>今日の天気予報</h2>
    <div class="flex gap-10 overflow-x-scroll w-full py-12">
      <div v-for="(hourData, index) in forecast.forecastday[0].hour" :key="index" class="">
        <!-- {{ hourData.time }} -->
        <p class="whitespace-nowrap text-md text-center">
          {{ new Date(hourData.time).getHours() + '時' }}
        </p>
        <div class="w-[50px] my-6">
          <img :src="hourData.condition.icon" alt="" />
        </div>
        <p class="text-md text-center">{{ Math.round(hourData.temp_c) }}&deg;</p>
      </div>
    </div>
    <hr class="w-full h-1 mx-auto my-4 bg-gray-200 border-0 rounded md:my-10 dark:bg-gray-700" />
    <h2>週間天気予報</h2>
    <div class="max-w-screen-md w-full py-12">
      <div
        v-for="(dayData, index) in forecast.forecastday"
        :key="index"
        class="flex gap-12 mt-6 items-center justify-between"
      >
        <p>
          {{ dayInWeek[new Date(dayData.date).getDay()] + '曜日' }}
        </p>
        <img :src="dayData.day.condition.icon" alt="" />
        <div>
          <div>
            最高{{ Math.round(dayData.day.maxtemp_c) }}&deg; 最低{{
              Math.round(dayData.day.mintemp_c)
            }}&deg;
          </div>
        </div>
        <div>降水確率: {{ dayData.day.daily_chance_of_rain }}%</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import axios from 'axios'
import { useRoute } from 'vue-router'

const route = useRoute()
const locationId = route.params.id
const dayInWeek = ['日', '月', '火', '水', '木', '金', '土']
console.log('locationid is', locationId)
const getLocalWeather = async () => {
  try {
    const result = await axios.get(
      `http://api.weatherapi.com/v1/forecast.json?key=01310cb2121b4b32ab181800240306&q=id:${locationId}&days=7&aqi=no&alerts=no`
    )
    return result.data
  } catch (err) {
    console.log(err)
  }
}
const { location, current, forecast } = await getLocalWeather()
// console.log(locationWeather)
</script>
