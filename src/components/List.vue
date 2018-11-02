<template>
  <div>
    <h2>Show list</h2>
    <ul class="list-group">
      <li class="list-group-item" v-for="item in todoItems" v-bind:key="item.id">{{item.text}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'list',
  props: {
    todoItems: Array
  }
};
</script>

<style>
</style>
