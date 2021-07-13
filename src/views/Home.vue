<template>
  <div class="wrapper">
    <div class="header">
      Text Editor
    </div>
    <div class="main">
      <div class="canvas-wrapper">
        Canvas
      </div>
      <Menu />
    </div>
  </div>
</template>

<script>
  import Menu from "../components/Menu"

  export default {
    name: 'Home',
    components: {
      Menu
    }
  }
</script>

<style scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    height: 100vh;
  }
  .header {
    font-family: 'Impact', sans-serif;
    text-align: center;
    padding: 15px 0 14px;
    background-color: #3ac888;
    color: #fff;
    font-size: 1.5rem;
    font-weight: bold;
    word-spacing: 11px;
  }
  .main {
    display: flex;
    justify-content: flex-end;
    height: 100%;
  }
  .canvas-wrapper {
    background-color: #e1e1e1;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-grow: 1;
  }
</style>
