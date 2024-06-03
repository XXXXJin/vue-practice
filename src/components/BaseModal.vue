<template>
  <Teleport to="body">
    <div v-show="isModelActice" class="absolute top-0 left-0 w-full h-screen bg-black bg-opacity-30">
      <div class="p-4 bg-white mt-32 mx-auto w-3/4 border border-gray-200 rounded shadow">
        <slot/>
        <button type="button" class="text-white bg-gray-800 hover:bg-gray-700 focus:ring-4 focus:ring-blue-300 rounded-lg px-3 py-2 me-2 mb-2 focus:outline-none text-xs mt-6 " v-on:click="$emit('close-modal')">閉じる</button>
      </div>
    </div>
  </Teleport>
</template>

<script setup>
  defineProps({
    isModelActice: {
      type: Boolean,
      default: false
    }
  });

  defineEmits(["close-modal"])
</script>