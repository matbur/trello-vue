<template>
  <ul>
    <task v-for="task in tasks" :key="task.id">
      {{task}}
    </task>
  </ul>
</template>

<script>
  import Task from './Task.vue'

  export default {
    props: ['tasks'],
    components: {Task},
  }
</script>

<style>
  ul {
    background-color: steelblue;
  }
</style>