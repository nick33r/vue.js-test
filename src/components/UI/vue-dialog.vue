<template>
  <dev class="dialog" v-if="show">
    <div class="dialog__content">
      <slot></slot>
    </div>
  </dev>
</template>

<script>
export default {
  name: 'vue-input',
  props: {
    show: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style>
  .dialog {
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.5);
    position: fixed;
    display: flex;
  }

  .dialog__content {
    margin: auto;
    background-color: white;
    border-radius: 12px;
    min-height: 50px;
    min-width: 300px;
  }
</style>