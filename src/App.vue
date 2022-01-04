<template>
  <div id="app">
    <div id="header">
      <Search v-on:query-change="querySearch" />
    </div>

    <div id="main-container">
      <h2>Todo-List</h2>
      <TodoAdd v-on:add-todo="addTodo" />
      <Todos v-bind:todosList="copyTodos" v-on:delete-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import Search from "./components/Search";
import TodoAdd from "./components/TodoAdd";
import Todos from "./components/Todos";

export default {
  name: "app",
  components: {
    Todos,
    TodoAdd,
    Search,
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id != id);
      this.copyTodos = [...this.todos];
    },
    addTodo(todo) {
      this.todos.push(todo);
      this.copyTodos = [...this.todos];
    },
    querySearch(query) {
      if (query.trim() === "") {
        this.copyTodos = [...this.todos];
      } else {
        const temp = this.todos.filter((todo) => {
          return todo.title.includes(query);
        });
        this.copyTodos = [...temp];
      }
    },
  },
  data() {
    return {
      todos: [
        {
          id: 0,
          title: "Comprar la cena",
          completed: false,
        },
        {
          id: 1,
          title: "Pasear al perro",
          completed: true,
        },
        {
          id: 2,
          title: "Jugar con el gato",
          completed: true,
        },
        {
          id: 3,
          title: "Lavar los platos",
          completed: false,
        },
      ],
      copyTodos: [],
    };
  },
  created() {
    this.copyTodos = [...this.todos];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Licorice&family=Titillium+Web:wght@200&display=swap");
#app {
  font-family: "Titillium Web", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 1.5em;
}

#main-container {
  border: solid 10px #ccc;
  width: 80%;
  margin: 100px auto;
}
#header {
  background: #ece0e3;
  padding: 0.5em;
  width: 50%;
  margin: 100px auto;
}

@import url("https://fonts.googleapis.com/css2?family=Licorice&display=swap");
h2 {
  font-family: "Licorice", cursive;
  font-size: 70px;
}
</style>
