<template>
  <div class="todo-vue">
    <vue-dialog :show="true"></vue-dialog>
    <todoForm @create="createTodos"/>
    <todoList :posts="posts" @remove="removeTodo"/>
  </div>
</template>

<script>
import todoForm from "@/components/todo-form.vue";
import todoList from "@/components/todo-list.vue";
export default {
  components: {
    todoForm, todoList
  },
  data() {
    return {
      posts: [
        {id: 0, title: 'Полить кактус', body: 'Чтобы он не помер'},
        {id: 1, title: 'Заправить кровать', body: 'Чтобы она была красивой'},
        {id: 2, title: 'Почистить обувь', body: 'Чтобы аж блестела'}
      ]
    }
  },
  methods: {
    createTodos(data) {
      this.posts.push(data);
    },
    removeTodo(todo) {
      this.posts = this.posts.filter(p => p.id !== todo.id)
    }
  }
}


</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
}

.container {
  display: flex;
  gap: 15px;
  align-items: center;
  flex-direction: column;
}
</style>