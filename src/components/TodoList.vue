<script setup lang="ts">
import {ref} from "vue";
import type {Todo} from "@/schemas/todo.ts";
import TodoItem from "@/components/TodoItem.vue";
import AddTodo from "@/components/AddTodo.vue";

const todos = ref<Todo[]>([])

let id = 0;

function insertTodo(newTodoTxt: string) {
  todos.value.push({
    id: id++,
    text: newTodoTxt
  })

}

function removeTodo(todo: Todo) {
  todos.value = todos.value.filter(e => e.id !== todo.id)

}

</script>

<template>
  <div class="flex flex-col gap-4">
    <div class="text-xl">TODO list</div>
    <AddTodo @on-add="(el) => insertTodo(el)"/>

    <ul class="flex flex-col gap-4">
      <li v-for="todo in todos" :key="todo.id">
        <TodoItem :id="todo.id" :text="todo.text" @delete-todo="(el) => removeTodo(el)"/>
      </li>
    </ul>
  </div>
</template>

