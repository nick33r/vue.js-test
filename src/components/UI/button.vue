<template>
  <button class="vue-button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'VueButton'
}
</script>

<style>
  .vue-button {
    padding: 8px 25px;
    border: 2px solid #3f3f3f;
    background-color: #3f3f3f28;
    cursor: pointer;
  }

  .vue-button:hover {
    background-color: #3f3f3f74;
    transform: scale(1.02);
  }
</style>