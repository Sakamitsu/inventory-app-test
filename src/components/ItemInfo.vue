<script setup lang="ts">

  import { ref } from 'vue';
  import Item from '../models/Item'

  const isDeleteItem = ref<boolean>(false);
  const inputValue = ref<number>();
  
  const props = defineProps<{
    item?: Item
  }>()

  const emit = defineEmits<{
    (e: "close"): void
    (e: "decreaseQuantity", quantity: number): number
  }>()

  const deleteItem = () => {
    if (inputValue === undefined || Number(inputValue) > Number(props.item?.quantity)) {
      return
    }
    emit("decreaseQuantity", Number(inputValue.value))
    emit("close")
  }
</script>

<template>
  <div class="item-info">
    <div 
      class="cross"
      @click="emit('close')"
    >
      <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 1.05L10.95 0L6 4.95L1.05 0L0 1.05L4.95 6L0 10.95L1.05 12L6 7.05L10.95 12L12 10.95L7.05 6L12 1.05Z" fill="white"/>
      </svg>
    </div>
    <div class="container">
      <div class="first"  :style="{ backgroundColor: `color-mix(in srgb, ${item?.color} 88%, white)` }"></div>
      <div class="second" :style="{ backgroundColor: `color-mix(in srgb, ${item?.color} 100%, white)` }"></div>
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
    <button
      v-if="isDeleteItem === false"
      @click="isDeleteItem = true"
    >
      Удалить предмет
    </button>
    <div 
      v-else
      class="delete-block"
    >
      <input 
        type="number" 
        placeholder="Введите количество"
        v-model="inputValue"
      >
      <div class="two-buttons">
        <button 
          class="cancel"
          @click="emit('close')"
        >
          Отмена
        </button>
        <button 
          class="confirm"
          @click="deleteItem"
        >
          Подтвердить
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import '../assets/style.scss';
  .item-info {
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 16px;
    width: 250px;
    height: 495px;
    background-color: $bg-black;
    z-index: 2;
    right: 0;
    color: white;
    border: 2px solid $border-color;
    opacity: 95%;
   
    & .container {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 10px;
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
      border-top: 1px solid $border-color;
    }

    & .skeletons {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      gap: 16px;
      & * {
        background-color: $bg-gray;
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
      cursor: pointer;
    }

    & .delete-block {
      bottom: 15px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 20px;
      & input {

        width: 210px;
        height: 35px;
        border-radius: 4px;
        background-color: $bg-black;
        border: 2px solid $border-color;
        color: white;
        outline: none;
        margin-top: 0;
        text-align: center;
      }

      & .two-buttons {
        display: flex;
        gap: 10px;

        & .cancel {
          width: 88px;
          height: 33px;
          background-color: white;
          color: black;
        }
        & .confirm {
          width: 112px;
          height: 33px;
        }
      }
    }
  }
</style>
