<template>
  <div class="todos">
    <div class="todos__content">
      <h3>{{ todo.title }}</h3>
      <div>{{ todo.body }}</div> 
    </div>
    <VueButton @click="$emit('remove', todo)">Готово!</VueButton>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
  .todos {
    border: 2px solid #3f3f3f;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 15px;
    inline-size: 500px;
  }

  .todos__content {
    inline-size: 100%;
    text-align: center;
  }
</style>