<template>
  <div id="app">
    <Category :cat="0" :tasks="tasks" @add="addTask"></Category>
  </div>
</template>

<script>
  import Category from './components/Category.vue'

  let store = {
    tasks: [
      {id: 0, text: 'task0', category: 0},
      {id: 1, text: 'task1', category: 0}
    ],
  }

  export default {
    name: 'app',
    components: {Category},
    data() {
      return store
    },
    methods: {

      addTask(category, text) {
        console.log('text from app', category, text)

        if (text === '') {
          return
        }

        const newTask = {id: this.tasks.length, text, category};
        this.tasks.push(newTask)
      }
    }
  }
</script>

<style>
</style>
