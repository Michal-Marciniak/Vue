<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <!-- Przekazujemy todos z data() jako props, do komponentu Todos -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <!-- Renderujemy komponent -->
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";

export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
  },
  // data to miejsce gdzie będziemy przechowywać
  // dane z todos
  data() {
    return {
      // todos to tablica obiektów todo
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      // ... oznacza, że kopiujemy wszystko z tablicy todos
      this.todos = [...this.todos, newTodo];
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline block;
  border: none;
  background: #4e4545;
  color: beige;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: dimgray;
}
</style>
