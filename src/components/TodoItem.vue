<template>
  <li>
    {{ title }}
    <button type="button" class="btn btn-dark" v-on:click="$emit('remove')">Remove</button>
  </li>
</template>

<script>
export default {
  name: 'todo-item',
  props: ['title']
};
</script>

<style>
</style>
