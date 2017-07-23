<template>
  <div id="app">
    <category v-for="cat in categories"
              :key="cat.id"
              :cat="cat"
              :tasks="getTasks(cat)"
              @addTask="addTask"
              @changeHeader="changeHeader"
    ></category>


    <div>
      <a href="#" v-if="!visibleInput" @click="changeInput">Add a list...</a>
      <div v-if="visibleInput">
        <input type="text"
               v-model="newCat"
               @blur="changeInput">
        <button @click="addCategory">Save</button>
        <button @click="newCat = ''">x</button>
      </div>
    </div>

  </div>
</template>

<script>
  import Category from './components/Category.vue'
  import store from './data'

  export default {
    name: 'app',
    components: {Category},
    data() {
      return Object.assign({}, store, {
        newCat: '',
        visibleInput: false,
      })
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
        this.newCat = ''
      },
      getTasks(cat) {
        return this.tasks.filter(task => task.category === cat.id)
      },
      changeInput(){
        this.visibleInput = !this.visibleInput
      },
      changeHeader(category, newName) {
        this.categories[category].name = newName
      },
    }
  }
</script>

<style>
  #app {
    background-color: #0079BF;
  }
</style>
