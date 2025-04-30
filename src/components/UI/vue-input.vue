<template>
  <input 
    :value="modelValue"
    @input="updateInput"
    class="vue-input"
    type="text" 
  >
</template>

<script>
export default {
  name: 'vue-input',
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value) 
    }
  }
}
</script>

<style scoped>
  .vue-input {
    inline-size: 500px;
    padding: 12px 20px;
    border: 2px solid #3f3f3f;
  }
</style>