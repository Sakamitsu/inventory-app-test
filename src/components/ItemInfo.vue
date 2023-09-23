<script setup lang="ts">
</script>

<template>
  <div class="item-info">
    <div class="cross">
      <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 1.05L10.95 0L6 4.95L1.05 0L0 1.05L4.95 6L0 10.95L1.05 12L6 7.05L10.95 12L12 10.95L7.05 6L12 1.05Z" fill="white"/>
      </svg>
    </div>
    <div class="container">
      <div class="first"  :style="{ backgroundColor: `color-mix(in srgb, green 88%, white)` }"></div>
      <div class="second" :style="{ backgroundColor: `color-mix(in srgb, green 100%, white)` }"></div>
    </div>
    <hr>
    <div class="skeletons">
      <div class="stub-1"></div>
      <div class="stub-2"></div>
      <div class="stub-3"></div>
      <div class="stub-4"></div>
      <div class="stub-5"></div>
      <div class="stub-6"></div>
    </div>
    <hr>
    <button>Удалить предмет</button>
  </div>
</template>

<style lang="scss" scoped>
  .item-info {
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 16px;
    width: 250px;
    height: 495px;
    background-color: #262626;
    z-index: 2;
    right: 0;
    color: white;
    border: 2px solid #4D4D4D;
    opacity: 95%;
   
    & .container {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: red;
      margin-bottom: 30px;
      & .first {
        width: 115px;
        height: 115px;
      }
      & .second {
        position: absolute;
        width: 115px;
        height: 115px;
        z-index: 1;
        right: 20px;
        top: 18px;
      }
    }
    hr {
      width: 90%;
      border: 0;
      border-top: 1px solid #4D4D4D;
    }

    & .skeletons {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      gap: 16px;
      & * {
        background-color: #3C3C3C;
        border-radius: 4px;
      }
      & .stub-1 {
        width: 211px;
        height: 30px;
        border-radius: 8px;
      }
      & .stub-2, & .stub-3, & .stub-4 {
        width: 211px;
        height: 10px;
      }
      & .stub-5 {
        width: 180px;
        height: 10px;
      }
      & .stub-6 {
        width: 80px;
        height: 10px;
      }
    }
    & button {
      width: 220px;
      height: 39px;
      background-color: #FA7272;
      color: white;
      border: none;
      border-radius: 8px;
    }
    & .cross {
      position: absolute;
      display: flex;
      justify-content: center;
      align-items: center;
      top: 8px;
      right: 8px;
      width: 24px;
      height: 24px;
    }
  }
</style>
