<template>
  <div class="container">
    <img src="../assets/img-blur.png" alt="img-blur">
    <div class="skeletons">
      <div class="stub-1"></div>
      <div class="stub-2"></div>
      <div class="stub-3"></div>
      <div class="stub-4"></div>
      <div class="stub-5"></div>
      <div class="stub-6"></div>
      <div class="stub-7"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import '../assets/style.scss';
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 18px;
    width: 236px;
    height: 500px;
    background-color: $bg-black;
    color: white;
    border: 2px solid $border-color;
    border-radius: 12px;
    & .skeletons {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      gap: 16px;
      width: 190px;
      height: 198px;
      & * {
        background-color: $bg-gray;
        border-radius: 4px;
      }
      & .stub-1 {
        width: 190px;
        height: 26px;
        border-radius: 8px;
      }
      & .stub-2 {
        width: 155px;
        height: 10px;
      }
      & .stub-3 {
        width: 190px;
        height: 10px;
      }
      & .stub-4 {
        width: 170px;
        height: 10px;
      }
      & .stub-5 {
        width: 160px;
        height: 10px;
      }
      & .stub-6 {
        width: 140px;
        height: 10px;
      }
      & .stub-7 {
        width: 80px;
        height: 10px;
      }
    }
  }
</style>