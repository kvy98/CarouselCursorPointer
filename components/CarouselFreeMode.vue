<template>
  <div class="wrapper-container">
    <flicking :options="options">
      <div class="panel">1</div>
      <div class="panel">2</div>
      <div class="panel">3</div>
      <div class="panel">4</div>
      <div class="panel">5</div>
    </flicking>
  </div>
</template>
<script>
export default {
  data() {
    return {
      options: {
        circular: true,
        moveType: 'freeScroll',
        align: 'prev',
        panelsPerView: 3,
      },
      cursorStyle: {
        top: '0px',
        left: '0px',
        display: 'none',
      },
    }
  },
}
</script>
<style lang="scss" scoped>
.wrapper-container {
  position: relative;
  .cursor-pointer {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    position: absolute;
    background-color: blue;
    z-index: 3;
  }
}
.panel {
  background: red;
  height: 100px;
  margin: 0 10px;
}
</style>
