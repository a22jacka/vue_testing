<script lang="js">
export default {
  name: "TODOList",
  data: function () {
    return {
      todos: [],
      todoText: '',
    };
  },
  methods: {
    addTodo: function () {
      //adds to array and updates localstorage
      this.todos = [...this.todos, this.todoText];
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
    removeTodo: function (i) {
      //removes from array and updates localstorage
      this.todos.splice(i, 1);
      localStorage.setItem('todos', JSON.stringify(this.todos));
      console.log("removed index " + i);
    }
  },
  mounted: function () {
    //gets localstorage on startup
    const existingTodos = localStorage.getItem('todos');
    this.todos = JSON.parse(existingTodos) || [];
  }
};
</script>

<template>
  <h1>Todo list</h1>
  <div class="tooltip">
    i<span class="tooltiptext">list items are stored in local storage</span>
  </div>
  <div>
    <ul>
      <li v-for="todo in todos" v-bind:key="todo">
        <button @click="removeTodo(todos.indexOf(todo))">X</button>
        {{ todo }}
      </li>
    </ul>

    <form v-on:submit.prevent="addTodo()">
      <input v-model="todoText" placeholder="What needs to be done">
      <button type="submit">Add todo</button>
    </form>
  </div>
</template>

<style scoped lang="scss">
@use '../assets/base.css';

h1 {
  color: var(--color-heading);
  display: inline-block;
}

.tooltip {
  position: relative;
  display: inline-block;
  color: var(--color-heading);
  font-size: 18pt;
  margin-left: .6em;
}

.tooltip .tooltiptext {
  visibility: hidden;
  position: absolute;
  top: -5px;
  left: 105%;
  background-color: var(--color-background-mute);
  z-index: 1;
  text-align: center;
  padding: .2em;
  color: var(--color-text);
  border-radius: .2em;
  font-size: 12pt;
  width: 17em;
}

@media (hover: hover) {
  .tooltip:hover .tooltiptext {
    visibility: visible;
  }
}
</style>