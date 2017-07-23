<template>
  <div id="app">
    <category v-for="cat in categories"
              :key="cat.id"
              :cat="cat.id"
              :name="cat.name"
              :tasks="getTasks(cat.id)"
              @add="addTask">
    </category>

    <input type="text" v-model="newCat">
    <button @click="addCategory">Add a list...</button>
  </div>
</template>

<script>
  import Category from './components/Category.vue'
  import store from './data'

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
      },
      getTasks(cat) {
        return this.tasks.filter(task => task.category === cat)
      }
    }
  }
</script>

<style>
  #app {
    background-color: #0079BF;
  }
</style>
