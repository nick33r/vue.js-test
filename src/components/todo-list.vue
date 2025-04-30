<template>
  <div class="container" v-if="posts.length > 0">
      <h2>Список дел</h2>
      <todoItem 
        class="todos" 
        v-for="todo in posts"
        :todo="todo"
        :key="todo.id"
        @remove="$emit('remove', todo)"
      />
  </div>
  <h2 style="color: lawngreen; text-align: center;" v-else>Вы сделали все дела! Молодцы!</h2>
</template>

<script>
import todoItem from "@/components/todo-item.vue";
export default {
  components: {
    todoItem
  },
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style>
  
</style>