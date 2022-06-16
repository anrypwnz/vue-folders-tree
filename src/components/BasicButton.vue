<template>
  <button @click="click">
    {{label}}
  </button>
</template>

<script>
export default {
  name: 'BasicButton',
  props: {
    label: String,
    click: Event
  },
}
</script>

<style scoped>
button {
  padding: 4px 8px;
  border-radius: 5px;
  cursor: pointer;
  margin: 0 12px;
}
</style>
