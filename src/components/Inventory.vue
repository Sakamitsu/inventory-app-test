<script setup lang="ts">
  import { ref } from 'vue'
  import ItemInfo from './ItemInfo.vue'
  
  interface Item {
    id: number
    isEmpty: boolean
    color: string
    quantity: number
  }
  
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

  // function getRandomColor() {
  //   let color = "hsl(" + Math.random() * 360 + ", 100%, 75%)";
  //   return color;
  // }

  const startDrag = (event: DragEvent, draggedItem: Item) => {
    console.log(draggedItem.id)
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

    console.log(droppedItem.id)
  }

  const showItemInfo = () => {
    isShowItemInfo.value = true;
  }
</script>

<template>
  <div class="inventory">
    <ItemInfo 
      v-if="isShowItemInfo"
    />
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
          @click="showItemInfo" 
        >
          <div 
            class="container"
            v-if="!item.isEmpty"
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
      border: 2px solid #4D4D4D;
      border-radius: 12px;
      background-color: #262626;
      & td, th {
        position: relative;
        color: white;
        border: 2px solid #4D4D4D;
        span {
          position: absolute;
          bottom: 0px;
          right: 0px;
          width: 16px;
          height: 16px;
          border-top: 2px solid #4D4D4D;
          border-left: 2px solid #4D4D4D;
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
  }
</style>