<template>
  <div id="app">
    <category v-for="cat in categories"
              :key="cat.id"
              :cat="cat.id"
              :name="cat.name"
              :tasks="tasks"
              @add="addTask">
    </category>

    <input type="text" v-model="newCat">
    <button @click="addCategory">Add a list...</button>
  </div>
</template>

<script>
  import Category from './components/Category.vue'

  let store = {
    tasks: [
      {id: 0, text: 'task0', category: 0},
      {id: 1, text: 'task1', category: 0},
      {id: 2, text: 'task2', category: 1},
      {id: 3, text: 'task3', category: 2},
    ],
    categories: [
      {id: 0, name: 'backlog'},
      {id: 1, name: 'ongoing'},
      {id: 2, name: 'done'},
    ]
  }

  export default {
    name: 'app',
    components: {Category},
    data() {
      return Object.assign({newCat: 'new category'}, store)
    },
    methods: {
      addTask(category, text) {
        console.log('text from app', category, text)
        if (text === '') {
          return
        }
        const newTask = {id: this.tasks.length, text, category};
        this.tasks.push(newTask)
      },
      addCategory() {
        console.log(this.newCat)
        if (this.newCat === '') {
          return
        }
        const newCat = {id: this.categories.length, name: this.newCat}
        this.categories.push(newCat)
      }
    }
  }
</script>

<style>
  #app {
    background-color: #0079BF;
  }
</style>
