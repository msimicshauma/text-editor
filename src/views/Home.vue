<template>
  <div class="wrapper">
    <div class="header">
      Text Editor
    </div>
    <div class="main">
      <div class="canvas-wrapper">
        Canvas
      </div>
      <div class="menu-wrapper">
        <span class="menu-header">Text Layer</span>
        <hr class="break">
        <div class="flex justify-between">
          <div class="flex flex-col flex-grow">
            <label for="entertext">Enter text</label>
            <input type="text" id="entertext" name="entertext">
          </div>
          <div class="plus-button">
            +
          </div>
        </div>
        <div class="flex justify-between">
          <div class="flex flex-col width-115 margin-top-25">
            <label for="fontsize">Font size</label>
            <input type="text" id="fontsize" name="fontsize">
          </div>
          <div class="flex flex-col width-115 margin-top-25">
            <label for="lineheight">Line height</label>
            <input type="text" id="lineheight" name="lineheight">
          </div>
        </div>
        <div class="flex flex-col margin-top-25 relative">
          <label for="cars">Change font family</label>
          <select
            id="cars"
            class="margin-top-5"
          >
            <option value="roboto">Roboto</option>
          </select>
          <img
            src="/src/assets/icons/caret-down.svg"
            class="caret-down"
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    components: {}
  }
</script>

<style scoped>
  .flex {
    display: flex;
  }
  .flex-col {
    flex-direction: column;
  }
  .flex-grow {
    flex-grow: 1;
  }
  .justify-between {
    justify-content: space-between;
  }
  .relative {
    position: relative;
  }

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
  .menu-wrapper {
    font-family: 'Arial', sans-serif;
    background-color: #fff;
    padding: 25px 20px;
    width: 250px;
  }
  .menu-header {
    color: #797979;
    font-weight: 600;
    font-size: 18px;
    padding-bottom: 11px;
  }
  .break {
    background-color: #e5e5e5;
    border: 0;
    height: 2px;
    margin: 12px 0;
  }
  label {
    font-size: 14px;
    color: #5d5d5d;
  }
  input {
    height: 19px;
    padding: 0 5px;
    border: 2px solid #e5e5e5;
    border-radius: 5px;
    outline: none;
    margin-top: 5px;
  }
  .width-115 {
    width: 115px;
  }
  .margin-top-5 {
    margin-top: 5px;
  }
  .margin-top-25 {
    margin-top: 25px;
  }
  .plus-button {
    height: 23px;
    width: 23px;
    line-height: 23px;
    text-align: center;
    vertical-align: middle;
    border-radius: 5px;
    align-self: flex-end;
    cursor: pointer;
    background-color: #3ac888;
    color: #fff;
    font-size: 19px;
    font-weight: bold;
    margin-left: 15px;
  }
  select {
    appearance: none;
    border: 2px solid #e5e5e5;
    padding: 3px 5px;
    border-radius: 5px;
    outline: none;
  }
  .caret-down {
    position: absolute;
    bottom: 0;
    right: 0;
  }
</style>
