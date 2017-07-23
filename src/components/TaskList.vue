<template>
  <ul>
    <li v-for="task in props.tasks">{{task}}</li>
  </ul>
</template>

<script>
  export default {
    props: ['tasks']
  }
</script>

<style>
  ul {
    background-color: steelblue;
  }
</style>