<script>
export default {
  name: 'GreetingComponent',
  props: ['name'],
  inheritAttrs: false
}
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-bind="$attrs">message 1</p>
    <p>message 2</p>
  </div>
</template>
