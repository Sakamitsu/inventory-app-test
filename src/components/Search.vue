<template>
  <div class="search">
    <div class="skeleton"></div>
    <div class="cross">
      <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 1.05L10.95 0L6 4.95L1.05 0L0 1.05L4.95 6L0 10.95L1.05 12L6 7.05L10.95 12L12 10.95L7.05 6L12 1.05Z" fill="white"/>
      </svg>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .search {
    position: relative;
    display: flex;
    align-items: center;
    width: 785px;
    height: 72px;
    background-color: #262626;
    border: 2px solid #4D4D4D;
    border-radius: 12px;
    & .skeleton {
      background-color: #3C3C3C;
      width: 699px;
      height: 36px;
      border-radius: 12px;
      margin-left: 18px;
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