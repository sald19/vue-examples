<style module src="./styles.module.css"></style>

<template>
  <div :class="$style.container">
    <h1 :class="$style.title">Nerdify Todo {{ completedTodos }}</h1>
    <ul :class="$style.list">
      <li :class="$style.item" v-for="todo in todos" :key="todo.id">
        <input
          :class="$style.checkbox"
          v-model="todo.completed"
          type="checkbox"
          name="complete"
        />
        <span :class="{ [$style.completed]: todo.completed }">
          {{ todo.title }}
        </span>
        <span :class="$style.delete" @click="deleteTodo(todo.id)">Delete</span>
      </li>
    </ul>

    <form :class="$style.form" action>
      <input type="text" v-model="todo" />
      <button @click.prevent="addTodo">Add Todo</button>
    </form>
  </div>
</template>

<script>
import "./styles.module.css";
export default {
  name: "Todo",

  data() {
    return {
      todo: undefined,
      todos: [
        { id: 1, title: "Application design meeting", completed: false },
        { id: 2, title: "New web UI design project", completed: false },
        { id: 3, title: "Select best frontend framework", completed: false },
      ],
    };
  },

  computed: {
    completedTodos() {
      return this.todos.filter((todo) => !!todo.completed).length;
    },
  },

  methods: {
    addTodo(todo) {
      const todoId = this.todos.length + 1;
      this.todos.push({ id: todoId, title: this.todo, completed: false });

      this.todo = undefined;
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
  },
};
</script>
