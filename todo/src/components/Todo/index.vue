<style module src="./styles.module.css"></style>

<template>
  <div class="px-4">
    <h1 class="text-black text-2xl font-semibold mt-8">Work</h1>
    <div class="flex items-center">
      <div
        :class="[
          $style.slider,
          'flex-1',
          'w-auto',
          'h-1',
          'bg-black',
          'rounded',
        ]"
      ></div>
      <span class="text-xs ml-4">80%</span>
    </div>

    <ul class="mt-8">
      <li
        class="bg-white my-2 p-4 rounded"
        v-for="todo in todos"
        :key="todo.id"
      >
        <input
          class="mr-4"
          v-model="todo.completed"
          type="checkbox"
          name="complete"
        />
        <span>
          {{ todo.title }}
        </span>
        <span @click="deleteTodo(todo.id)">Delete</span>
      </li>
    </ul>

    <form action>
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
