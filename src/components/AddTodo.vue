<script setup lang="ts">

import {Button} from "@/components/ui/button";
import {Input} from "@/components/ui/input";
import {ref} from "vue";

const emit = defineEmits<{
  onAdd: [todoTxt: string]
}>()

const newTodo = ref("")

function addTodo() {
  emit("onAdd", newTodo.value)
  newTodo.value = ""
}

</script>

<template>
  <form @submit.prevent="addTodo" class="flex items-center gap-4">
    <Input required v-model="newTodo" placeholder="add a new todo..."/>
    <Button class="pi pi-plus shrink-0"></Button>
  </form>
</template>
