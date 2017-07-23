<template>
  <div class="list">
    <div>
      <h3 v-if="visibleHeader"
          v-text="name"
          @click="changeHeader"
      ></h3>
      <input type="text"
             v-if="!visibleHeader"
             v-model="name"
             @blur="changeHeader">
    </div>

    <div class="cards">
      <card v-for="task in tasks"
            :key="task.id"
            v-text="task.text"></card>

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
  import Card from './Card.vue'

  export default {
    props: ['cat', 'tasks'],
    components: {Card},
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
  .list {
    background-color: #E2E4E6;
    width: 300px;
    border-radius: 3px;
  }

  .cards {
    background-color: greenyellow; /*TODO: to remove*/
    width: 90%;
    margin: auto;
  }
</style>