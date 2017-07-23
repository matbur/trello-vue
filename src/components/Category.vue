<template>
  <div id="cat">
    <input type="text" v-model="inp_data" v-text="inp_data">
    <button @click="addTask">add task</button>

    <ul>
      <li v-for="task in tasks">{{task}}</li>
    </ul>
  </div>
</template>

<script>
  export default {
    props: ['cat', 'tasks'],
    data() {
      return {
        inp_data: 'dupa',
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