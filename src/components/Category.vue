<template>
  <div id="cat">
    <div>
      <h3 v-if="visibleHeader"
          v-text="name"
          @click="changeHeader"></h3>
      <input type="text"
             v-if="!visibleHeader"
             v-model="name"
             @blur="changeHeader">
    </div>

    <div class="tasks">
      <task v-for="task in tasks"
            :key="task.id"
            v-text="task.text"></task>

      <div v-if="visibleInput">
        <input type="text"
               v-model="inpData"
               @blur="changeInput">
        <button @click="addTask">Add</button>
        <button @click="inpData = ''">x</button>
      </div>
    </div>


    <a href="#" @click="changeInput">Add a card...</a>
  </div>
</template>

<script>
  import Task from './Task.vue'

  export default {
    props: ['cat', 'tasks'],
    components: {Task},
    data() {
      return {
        name: this.cat.name,
        id: this.cat.id,
        inpData: '',
        visibleHeader: true,
        visibleInput: false,
      }
    },
    methods: {
      addTask() {
        this.$emit('addTask', this.id, this.inpData)
        this.inpData = ''
      },
      changeHeader() {
        if (!this.visibleHeader) {
          this.$emit('changeHeader', this.id, this.name)
        }
        this.visibleHeader = !this.visibleHeader
      },
      changeInput() {
        this.visibleInput = !this.visibleInput
      }
    }
  }
</script>

<style>
  #cat {
    background-color: #E2E4E6;
    width: 300px;
    border-radius: 3px;
  }

  .tasks {
    background-color: greenyellow; /*TODO: to remove*/
    width: 90%;
    margin: auto;
  }
</style>