<script setup lang="ts">
</script>

<template>
  <div class="inventory">
    <table>
      <tr>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
      </tr>
      <tr>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
      </tr>
      <tr>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
      </tr>
      <tr>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
      </tr>
      <tr>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
      </tr>
    </table>
  </div>
</template>

<style lang="scss" scoped>
  .inventory {
    width: 525px;
    height: 500px;
    background-color: bisque;
    border: 2px solid #4D4D4D;
    border-radius: 12px;
    background-color: #262626;

    & table {
      height: 100%;
      width: 100%;
      margin: 0 auto;
      border-collapse: collapse;
      border-style: hidden;
      & td, th {
        text-align: center;
        color: white;
        border: 2px solid #4D4D4D;
      }
    }
  }
</style>