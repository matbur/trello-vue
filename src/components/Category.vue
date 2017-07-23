<template>
  <div id="cat">
    <h3>{{name}}</h3>
    <input type="text" v-model="inp_data" v-text="inp_data">
    <button @click="addTask">add task</button>

    <task-list :tasks="t"></task-list>
  </div>
</template>

<script>
  import TaskList from './TaskList.vue'

  export default {
    props: ['cat', 'tasks', 'name'],
    components: {TaskList},
    data() {
      return {
        inp_data: 'dupa',
      }
    },
    computed: {
      t() {
        return this.tasks.filter(task => task.category === this.cat)
      }
    },
    methods: {
      addTask() {
        this.$emit('add', this.cat, this.inp_data)
        this.inp_data = ''
      }
    }
  }
</script>

<style>
  #cat {
    background-color: yellow;
    width: 300px;
  }
</style>