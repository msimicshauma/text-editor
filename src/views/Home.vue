<template>
  <div class="wrapper">
    <div class="header">
      Text Editor
    </div>
    <div class="main">
      <div class="canvas-wrapper">
        <div
          class="container"
          @click="setMenuParams"
        >
          <canvas id="canvas"></canvas>
        </div>
      </div>
      <Menu
        ref="menu"
        @addTextField="addTextField"
        @updateTextboxConfig="updateTextboxProperty"
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
      addTextField(config) {
        const textboxConfig = {
          cornerStyle: 'circle',
          transparentCorners: false,
          cornerColor: '#fff',
          cornerStrokeColor: '#bababa',
          cornerSize: 10,
          borderColor: '#bababa',
          borderScaleFactor: 1.3
        }
        if (parseInt(config.fontSize)) textboxConfig.fontSize = config.fontSize
        if (parseInt(config.lineHeight)) textboxConfig.lineHeight = config.lineHeight
        if (config.fontFamily) textboxConfig.fontFamily = config.fontFamily

        const textbox = new fabric.IText(config.text, textboxConfig)
        this.fabricCanvas.add(textbox)
      },
      updateTextboxProperty(config) {
        const selectedTextbox = this.fabricCanvas.getActiveObject()
        if (selectedTextbox) {
          selectedTextbox.set(config.property, config.value)
          this.fabricCanvas.renderAll()
        }
      },
      setMenuParams() {
        const selectedTextbox = this.fabricCanvas.getActiveObject()
        if (selectedTextbox) {
          this.$refs.menu.fontSize = selectedTextbox.fontSize
          this.$refs.menu.lineHeight = selectedTextbox.lineHeight
          this.$refs.menu.fontFamily = selectedTextbox.fontFamily
        }
      }
    },
    mounted() {
      this.fabricCanvas = new fabric.Canvas('canvas')
      this.fabricCanvas.on('object:scaling', (event) => {
        event.target.fontSize *= event.target.scaleX
        event.target.fontSize = event.target.fontSize.toFixed(0)
        event.target.scaleX = 1
        event.target.scaleY = 1
        this.fabricCanvas.renderAll()
        this.setMenuParams()
      })
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
