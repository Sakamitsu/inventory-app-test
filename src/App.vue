<script setup lang="ts">
  import Menu from './components/Menu.vue'
  import Inventory from './components/Inventory.vue'
</script>

<template>
  <div class="app-container">
    <div class="row-container">
      <Menu/>
      <Inventory/>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .app-container {
    display: flex;
    align-items: center;
    justify-content: center;
    position:fixed;
    /* position: absolute; */
    padding:0;
    margin:0;
    top:0;
    left:0;

    width: 100%;
    height: 100%;
    background: #1E1E1E;
    & .row-container {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 24px;
    }
  }
</style>
