
<template>
  <div class="todo" v-bind:class="{ completed: todo.completed }">
    <div id="todo-body" v-bind:class="{ completed: todo.completed }">
      <input
        type="checkbox"
        v-bind:checked="todo.completed ? 'checked' : ''"
        v-on:change="checkTodo"
      />
      {{ todo.title }}
    </div>
    <div id="todo-actions">
      <button @click="$emit('delete-todo', todo.id)">Eliminar</button>
    </div>
  </div>
</template>
    


<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    checkTodo() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo {
  border-bottom: solid 1px #ccc;
  padding: 10px;
  font-size:1.5em;
}
.todo:not(.completed):hover {
  background-color: rgb(224, 208, 211);
}
.completed {
  color: #ccc;
  text-decoration: line-through;
}
.completed .todo-body {
  text-decoration: line-through;
}

.todo-body {
  width: 100%;

}
.todo-actions {
  padding: 0 10px;
  width: 10%;
}

button {
  border: none;
  border-radius: 2px;
  padding: 10px;
  background: #ccc;
  font-weight: bold;
  color: black;
  font-family: "Licorice", cursive;
  font-size: 30px;
}
button:hover {
  background-color: #ccc;
  color: black;
}
</style>
