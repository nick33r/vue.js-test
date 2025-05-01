<template>
  <div class="adder-container container">
      <vue-input 
        type="text" 
        placeholder="Новое дело"
        v-model="todo.title"
      />
      <vue-input 
        type="text"
        placeholder="Описание дела"
        v-model="todo.body"
      />
      <VueButton 
        class="adder-btn"
        @click="createTodo"
      >
        Добавить
      </VueButton>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createTodo() {
      if (this.todo.title && this.todo.body) {
        this.todo.id = Date.now();
        this.$emit('create', this.todo);
        this.todo = {
          title: '',
          body: ''
        }
      }
    }
  }
}
</script>

<style>
  .todo-vue {
  padding: 50px;
  display: flex;
  gap: 30px;
  flex-direction: column;
}

.adder-container {
  width: 400px;
  margin: auto;
}

.adder-container textarea {
  inline-size: 500px;
  padding: 12px 20px;
  border: 2px solid #3f3f3f;
}

.adder-container .vue-button {
  align-self: flex-end;
}
</style>