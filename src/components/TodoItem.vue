<script setup lang="ts">
import type {Todo} from "@/schemas/todo.ts";
import {Button} from "@/components/ui/button";
import {Card} from "@/components/ui/card";

const todo = defineProps<Todo>()

</script>

<template>
  <Card class="p-1 flex items-center">
    <div class="pl-4 text-sm">{{ todo.text }}</div>
    <div class="ml-auto"/>
    <Button @click="$emit('deleteTodo', todo)" variant="outline" class="pi pi-minus shrink-0"/>
  </Card>
</template>
