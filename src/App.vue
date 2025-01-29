<template>
  <h2>TODO List</h2>
  <form v-on:submit.prevent>
    <input type="text" v-model="newItem">
    <button v-on:click="addItem">Add</button>
  </form>
  <ul>
    <!-- eslint-disable-next-line -->
    <li v-for="(todo, index) in $data.todos">
      <input type="checkbox" v-model="todo.isDone">
      <span v-bind:class="{ done: todo.isDone }">{{ todo.item }}</span>
      <button v-on:click="deleteItem(index)">Delete</button>
    </li>
  </ul>
  <!-- <pre>{{ $data.todos }}</pre> -->
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    newItem: '',
    todos: []
  }),
  methods: {
    /* eslint-disable-next-line */
    addItem: function(event) {
      if(this.newItem === '') return
      let todo = {
        item: this.newItem,
        isDone: false
      }
      this.todos.push(todo)
      this.newItem = ''
    },
    deleteItem: function(index) {
      console.log(index)
      this.todos.splice(index, 1)
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

#app ul {
  list-style: none;
}

#app li > span.done {
  text-decoration: line-through;
}
</style>
