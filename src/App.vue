<template>
  <div class="todo-vue">
    <div class="header">
      <h1>Какие еще дела нужно сделать?</h1>
      <VueButton @click="showDialog">Новое дело</VueButton>
      <vue-select v-model="selectedSort" :options="sortOptions"></vue-select>
    </div>
    <vue-dialog v-model:show="dialogVisible">
      <todoForm @create="createTodos"/>
    </vue-dialog>
    <todoList :posts="posts" @remove="removeTodo" v-if="!isLoading"/>
    <div v-else style="text-align: center;">Загружаем дела...</div>
    <VueButton @click="fetchTodos">Получить новые дела!</VueButton>
  </div>
</template>

<script>
import todoForm from "@/components/todo-form.vue";
import todoList from "@/components/todo-list.vue";
import axios from "axios";

export default {
  components: {
    todoForm, todoList
  },
  data() {
    return {
      posts: [
        {id: '0cscdsc', title: 'Полить кактус', body: 'Чтобы он не помер'},
        {id: 'sdcsdvs', title: 'Заправить кровать', body: 'Чтобы она была красивой'},
        {id: '2dsvsds', title: 'Почистить обувь', body: 'Чтобы аж блестела'}
      ],
      dialogVisible: false,
      isLoading: false,
      selectedSort: '',
      sortOptions: [
        {value: title, name: 'По названию'},
        {value: body, name: 'По описанию'},
      ]
    }
  },
  methods: {
    createTodos(data) {
      this.posts.push(data);
      this.dialogVisible = false;
    },
    removeTodo(todo) {
      this.posts = this.posts.filter(p => p.id !== todo.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchTodos() {
      try {
        this.isLoading = true;
        const respons = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5');
        respons.data.forEach(todo => {
          this.posts.push(todo)
        });
      } catch (error) {
        alert('Ошибка!')
      } finally {
        this.isLoading = false;
      }
    }
  },
  mounted() {
    this.fetchTodos();
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

.header {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 15px;
}

.header .vue-button {
  inline-size: 500px;
}

.container {
  display: flex;
  gap: 15px;
  align-items: center;
  flex-direction: column;
}
</style>