<script setup lang="ts">
  import { ref } from 'vue'
  import ItemInfo from './ItemInfo.vue'
  import Item from '../models/Item'
  
  const items = ref<Item[]>([
    {id: 0,  isEmpty: false, color: "#7FAA65", quantity: 4},
    {id: 1,  isEmpty: false, color: "#AA9765", quantity: 2},
    {id: 2,  isEmpty: false, color: "#7481ED", quantity: 5},
    {id: 3,  isEmpty: true,  color: "",      quantity: 0},
    {id: 4,  isEmpty: true,  color: "",      quantity: 0},
    {id: 5,  isEmpty: true,  color: "",      quantity: 0},
    {id: 6,  isEmpty: true,  color: "",      quantity: 0},
    {id: 7,  isEmpty: true,  color: "",      quantity: 0},
    {id: 8,  isEmpty: true,  color: "",      quantity: 0},
    {id: 9,  isEmpty: true,  color: "",      quantity: 0},
    {id: 10, isEmpty: true,  color: "",      quantity: 0},
    {id: 11, isEmpty: true,  color: "",      quantity: 0},
    {id: 12, isEmpty: true,  color: "",      quantity: 0},
    {id: 13, isEmpty: true,  color: "",      quantity: 0},
    {id: 14, isEmpty: true,  color: "",      quantity: 0},
    {id: 15, isEmpty: true,  color: "",      quantity: 0},
    {id: 16, isEmpty: true,  color: "",      quantity: 0},
    {id: 17, isEmpty: true,  color: "",      quantity: 0},
    {id: 18, isEmpty: true,  color: "",      quantity: 0},
    {id: 19, isEmpty: true,  color: "",      quantity: 0},
    {id: 20, isEmpty: true,  color: "",      quantity: 0},
    {id: 21, isEmpty: true,  color: "",      quantity: 0},
    {id: 22, isEmpty: true,  color: "",      quantity: 0},
    {id: 23, isEmpty: true,  color: "",      quantity: 0},
    {id: 24, isEmpty: true,  color: "",      quantity: 0},
  ])

  const isShowItemInfo = ref<boolean>(false);
  
  const passItem = ref<Item|undefined>(undefined);

  // Генерация случайного светлого цвета на случай, если будет функционал добавления
  // function getRandomColor() {
  //   let color = "hsl(" + Math.random() * 360 + ", 100%, 75%)";
  //   return color;
  // }

  const startDrag = (event: DragEvent, draggedItem: Item) => {
    event.dataTransfer?.setData("draggedItemId", String(draggedItem.id))
  }
  const onDrop = (event: DragEvent, droppedItem: Item) => {
    if (!droppedItem.isEmpty) {
      return
    }
    const draggedItemId = event.dataTransfer?.getData("draggedItemId")
    let draggedItem = items.value.find((item) => item.id === Number(draggedItemId)) as Item
    if (draggedItem.isEmpty) {
      return
    }
    droppedItem.isEmpty = false;
    droppedItem.color = draggedItem.color;
    droppedItem.quantity = draggedItem.quantity;

    draggedItem.isEmpty = true;
    draggedItem.color = "";
    draggedItem.quantity = 0;
  }
  
  const showItemInfo = (item: Item) => {
    if (item.isEmpty) {
      return
    }
    isShowItemInfo.value = true;
    passItem.value = item;
  }
  const decreaseQuantity = (quantity: number) => {
    const item = items.value.find((item) => item.id === (passItem.value as Item).id) as Item
    item.quantity -= quantity;

    passItem.value = undefined;
  }

</script>

<template>
  <div class="inventory">
    <Transition name="slide-fade">
      <ItemInfo 
      v-if="isShowItemInfo"
      @close="isShowItemInfo = false"
      @decrease-quantity="decreaseQuantity"
      :item="passItem"
      />
    </Transition>
    <table>
      <tr
        v-for="rowNumber in [1,2,3,4,5]" 
        :key="rowNumber" 
      >
        <td
          v-for="item in items.filter((i) => i.id < 25*(rowNumber/5) && i.id >= 25*(rowNumber/5)-5 )" 
          :key="item.id"
          draggable="true"
          @dragstart="startDrag($event, item)"
          @drop="onDrop($event, item)"
          @dragenter.prevent
          @dragover.prevent
          @click="showItemInfo(item)" 
        >
          <div 
            class="container"
            v-if="!item.isEmpty && item.quantity>0"
          >
            <div class="first"  :style="{ backgroundColor: `color-mix(in srgb, ${item.color} 88%, white)` }"></div>
            <div class="second" :style="{ backgroundColor: `color-mix(in srgb, ${item.color} 100%, white)` }"></div>
          </div>
          <span 
            v-if="item.quantity>0"
          >
            {{ item.quantity }}
          </span>
        </td>
      </tr>
    </table>
  </div>
</template>

<style lang="scss" scoped>
  @import '../assets/style.scss';
  .inventory {
    position: relative;
    width: 525px;
    height: 500px;

    & table {
      height: 100%;
      width: 100%;
      margin: 0 auto;
      border-collapse: collapse;
      border-style: hidden;
      border: 2px solid $border-color;
      border-radius: 12px;
      background-color: $bg-black;
      & td, th {
        position: relative;
        color: white;
        border: 2px solid $border-color;
        cursor: pointer;
        span {
          position: absolute;
          bottom: 0px;
          right: 0px;
          width: 16px;
          height: 16px;
          border-top: 2px solid $border-color;
          border-left: 2px solid $border-color;
          border-top-left-radius: 6px;
          padding: 2px;
          color: #7D7D7D;
          font-family: "Inter";
        }

        & .container {
          position: relative;
          display: flex;
          justify-content: center;
          align-items: center;
          width: 100%;
          height: 100%;
          & .first {
            width: 48px;
            height: 48px;
          }
          & .second {
            position: absolute;
            width: 48px;
            height: 48px;
            z-index: 1;
            right: 20px;
            top: 18px;
          }
        }
      }
      & td {
        width: 105px;
        height: 95px;
      }
    }
    .slide-fade-enter-active {
      transition: all 0.3s ease-out;
    }
    .slide-fade-leave-active {
      transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
    }
    .slide-fade-enter-from, .slide-fade-leave-to {
      transform: translateX(20px);
      opacity: 0;
    } 
  }
</style>