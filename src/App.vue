<template>
  <div id="app">
    <!--<Category tasks="store.tasks"></Category>-->
    <input type="text" v-model="store.inp_data" v-text="store.inp_data">
    <button @click="addTask">add task</button>
    <ul>
      <li v-for="task in store.tasks">{{task}}</li>
    </ul>
  </div>
</template>

<script>
  //  import Category from './components/Category.vue'

  let store = {
    tasks: [
      {id: 0, text: 'task0', category: 0},
      {id: 1, text: 'task1', category: 0}
    ],
    inp_data: ''
  }

  export default {
    name: 'app',
//    components: {Category},
    data() {
      return {
        store
      }
    },
    methods: {

      addTask: () => {
        const inp_data = store.inp_data

        if (inp_data === '') {
          return
        }

        const tasks = store.tasks
        const newTask = { id: tasks.length, text: inp_data, category: 0}

        tasks.push(newTask)
        store.inp_data = ''
      }
    }
  }
</script>

<style>
</style>
