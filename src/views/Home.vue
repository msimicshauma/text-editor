<template>
  <div class="wrapper">
    <div class="header">
      Text Editor
    </div>
    <div class="main">
      <div class="canvas-wrapper">
        <div class="container">
          <canvas
            id="canvas"
          ></canvas>
        </div>
      </div>
      <Menu
        @addTextField="addTextField"
      />
    </div>
  </div>
</template>

<script>
  import Menu from "../components/Menu"
  import { fabric } from 'fabric'

  export default {
    name: 'Home',
    components: {
      Menu
    },
    data() {
      return {
        fabricCanvas: null
      }
    },
    methods: {
      addTextField(newText) {
        const textField = new fabric.IText(newText, {
          cornerStyle: 'circle',
          transparentCorners: false,
          cornerColor: '#fff',
          cornerStrokeColor: '#bababa',
          cornerSize: 10,
          borderColor: '#bababa',
          borderScaleFactor: 1.3
        })
        this.fabricCanvas.add(textField)
      }
    },
    mounted() {
      this.fabricCanvas = new fabric.Canvas('canvas')
      this.fabricCanvas.setHeight(500)
      this.fabricCanvas.setWidth(500)
    }
  }
</script>

<style scoped>
  /* App wrapper and header */
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

  /* Main content section that wraps canvas and menu */
  .main {
    display: flex;
    justify-content: flex-end;
    height: 100%;
  }

  /* Canvas wrapper */
  .canvas-wrapper {
    background-color: #e1e1e1;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-grow: 1;
  }

  /* Canvas container */
  .container {
    background-color: #fff;
    border: 2px solid #cfcfcf;
    width: 500px;
    height: 500px;
  }
</style>
