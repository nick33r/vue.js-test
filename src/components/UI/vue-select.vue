<template>
  <select 
    class="vue-select" 
    v-model="modelValue"
    @change="changeOption"
  >
    <option disabled value="">Выберите из списка</option>
    <option 
      v-for="option in options" 
      value=""
      :key="option.value"
    >
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'vue-select',
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', option)
    }
  }
}
</script>

<style>
  .vue-select {
    padding: 8px 25px;
    border: 2px solid #3f3f3f;
    background-color: #3f3f3f28;
    cursor: pointer;
  }

  .vue-select:hover {
    background-color: #3f3f3f74;
  }
</style>