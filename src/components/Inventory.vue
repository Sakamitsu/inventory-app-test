<script setup lang="ts">
</script>

<template>
  <div class="inventory">
    <table>
      <tr>
        <td>
          1
          <span>4</span>
        </td>
        <td>
          2
          <span>5</span>
        </td>
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
        position: relative;
        text-align: center;
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
      }
    }
  }
</style>