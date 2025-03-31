<script setup lang="ts">
import {ref} from "vue";
import type {Todo} from "@/schemas/todo.ts";
import {Button} from "@/components/ui/button";

const todos = ref<Todo[]>([])

let id = 0;
const newTodo = ref("")

function addTodo() {
  todos.value.push({
    id: id++,
    text: newTodo.value
  })

  newTodo.value = ""
}

function removeTodo(id: number) {
  todos.value = todos.value.filter(e => e.id !== id)
}

</script>

<template>
  <div class="flex flex-col gap-4">
    <div class="text-xl">TODO list</div>
    <form @submit.prevent="addTodo">
      <input required v-model="newTodo" placeholder="add a new todo...">
      <Button />
    </form>
  </div>
</template>

