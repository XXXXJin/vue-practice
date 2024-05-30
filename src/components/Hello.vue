<script>
export default {
  name: 'GreetingComponent',
  props: ['name'],
  inheritAttrs: false,
  inject: ['username']
}
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-bind="$attrs">message 1</p>
    <p>message 2</p>
    <p>{{ `provided username is ${username}` }}</p>
  </div>
</template>
