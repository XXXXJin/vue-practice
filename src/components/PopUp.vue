<script>
export default {
  emits: ['closePopup']
}
</script>

<template>
  <div>
    <h2>this is the popup</h2>
    <button v-on:click="$emit('closePopup', 'secretss')">close the popup</button>
  </div>
</template>
