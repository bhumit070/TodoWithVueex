<template>
  <div>
    <h3>TODOs</h3>
    <div class="todos">
      <div
        class="todo"
        v-bind:class="{ completed: todo.completed }"
        :key="todo.id"
        v-for="todo in allTodos"
      >
        {{ todo.title }}
        <i @click="deleteTodo(todo.id)" class="fas fa-trash-alt delete"></i>
        <i @click="dblClick(todo)" class="fas fa-check check"></i>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    dblClick(todo) {
      const updatedTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      };
      this.updateTodo(updatedTodo);
    }
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>

<style>
.todos {
  max-width: 50%;
}
.fas {
  float: right;
  cursor: pointer;
}
.delete {
  color: red;
}
.check {
  margin-right: 20px;
  color: green;
}
.completed {
  text-decoration: line-through;
}
</style>
