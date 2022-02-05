<template>
  <header><h2>To-Do List</h2></header>
  <h4>New To-Do</h4>
  <textarea :value=item @input="onInput"></textarea>
  <br >
  <button :disabled='isDisabled' @click="addItem">Add Item</button>
  <br >
  <List :list=list />
</template>

<script>
import List from './components/List.vue';
export default {
  name: 'App',
  components: {
    List: List
  },
  data() {
    return {
      item: '',
      list: [{
        item: '',
        key: '',
      }],

    }
  },
  methods: {
    addItem() {
      this.list.push({
        item: this.item,
        key: this.randomNumber()
      });
      this.item='';
    },
    randomNumber() {
      return Math.floor(Math.random() * (10 - 1 + 1)) + 1
    },
    onInput(event) {
      this.item = event.target.value
    }
  },
  computed: {
    isDisabled() {
      return this.item.length === 0
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
