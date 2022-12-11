<script setup>
import Todo from "./component/Todo.vue"


</script>

<template>
 <div>

  <Todo />
  <button @click="$emit('someEvent')">click me</button>

 </div>
</template>

