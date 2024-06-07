<template>
  <Suspense>
    <AsyncCityView />
    <template #fallback>
      <p class="m-6">loading.....</p>
    </template>
  </Suspense>
</template>

<script setup>
import AsyncCityView from '@/components/AsyncCityView.vue'
</script>
