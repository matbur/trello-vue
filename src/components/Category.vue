<template>
  <div id="cat">
    <!--<input type="text" v-model="inp_data" v-text="inp_data">-->
    <!--<button @click="addtask">add task</button>-->
    <!--&lt;!&ndash;<task-list></task-list>&ndash;&gt;-->
    <!--<ul>-->
      <!--<li v-for="task in tasks">{{task}}</li>-->
    <!--</ul>-->
  </div>
</template>

<script>
  import TaskList from './TaskList.vue';

  export default {
    props: ['tasks'],
    components: {TaskList},
    data() {
      return {
        tasks: props.tasks
      }
    },
    methods: {
      addTask: (e) => {
        console.log(store)
        console.log(inp_data)
        store.tasks.push(inp_data)
        inp_data = ''
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