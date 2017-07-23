<template>
  <div id="cat">
    <h3>{{name}}</h3>

    <ul>
      <task v-for="task in t"
            :key="task.id"
            v-text="task.text"></task>
    </ul>

    <input type="text" v-model="inp_data">
    <button @click="addTask">Add a card...</button>
  </div>
</template>

<script>
  import Task from './Task.vue'

  export default {
    props: ['cat', 'tasks', 'name'],
    components: {Task},
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
    background-color: #E2E4E6;
    width: 300px;
  }

  ul {
    list-style: none;
  }
</style>