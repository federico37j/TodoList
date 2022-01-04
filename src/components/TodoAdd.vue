
<template>
  <div id="add-container">
    <form @submit="addTodo">
      <input type="text" v-model="title" />
      <button class="btn-enviar" v-on:input="$emit('query-change', query)">
        Enviar
      </button>
    </form>
  </div>
</template>

<script>
import { uuid } from "vue-uuid";

export default {
  name: "TodoAdd",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false,
      };
      this.title = "";
      this.$emit("add-todo", newTodo);
    },
  },
};
</script>
<style scoped>
#add-container {
  padding: 10px;
}

.btn-enviar {
  width: 50%;
  background: #ece0e3;
  font-size: 30px;
  font-family: "Licorice", cursive;
  font-weight: bold;
  font-size: 35px;
  border-radius: 4px;
  padding: 10px;
}

input {
  padding: 20px;
  outline: none;
  border: solid 1px #ccc;
  width: 90%;
}
</style>