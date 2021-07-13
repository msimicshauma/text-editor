<template>
  <div class="menu-wrapper">
    <span class="menu-header">Text Layer</span>
    <hr class="break">
    <div class="flex">
      <div class="big-input">
        <label for="elementText">Enter text</label>
        <input
          v-model="newElementText"
          type="text"
          id="elementText"
          name="elementText"
          placeholder="Text for new element"
          @keyup.enter="addNewElement"
        >
      </div>
      <div
        class="plus-button"
        @click="addNewElement"
      >
        +
      </div>
    </div>
    <div class="flex justify-between">
      <div class="small-input">
        <label for="fontSize">Font size</label>
        <input
          v-model="fontSize"
          type="number"
          id="fontSize"
          name="fontSize"
          placeholder="Font size (px)"
          @input="updateTextbox('fontSize')"
        >
      </div>
      <div class="small-input">
        <label for="lineHeight">Line height</label>
        <input
          v-model="lineHeight"
          type="number"
          id="lineHeight"
          name="lineHeight"
          placeholder="Line height (px)"
          @input="updateTextbox('lineHeight')"
        >
      </div>
    </div>
    <div class="option-container">
      <label for="fontFamily">Change font family</label>
      <select
        v-model="fontFamily"
        id="fontFamily"
      >
        <option value="roboto" selected>Roboto</option>
      </select>
      <img
        src="@/assets/icons/chevron-down.svg"
        class="chevron-down"
      >
    </div>
  </div>
</template>

<script>
  export default {
    name: "Menu",
    data() {
      return {
        newElementText: '',
        fontSize: '',
        lineHeight: '',
        fontFamily: 'roboto'
      }
    },
    methods: {
      addNewElement() {
        this.$emit('addTextField', this.newElementText)
        this.newElementText = ''
      },
      updateTextbox(property) {
        if (!parseInt(this[property])) return
        this.$emit('updateTextboxConfig', {
          property: property,
          value: parseInt(this[property])
        })
      }
    }
  }
</script>

<style scoped>
  /* Flexbox classes */
  .flex {
    display: flex;
  }
  .justify-between {
    justify-content: space-between;
  }

  /* Menu wrapper and header */
  .menu-wrapper {
    font-family: 'Arial', sans-serif;
    background-color: #fff;
    padding: 25px 20px;
    width: 250px;
    box-shadow: -9px 0px 7px 0px rgba(0,0,0,0.19);
  }
  .menu-header {
    color: #797979;
    font-weight: 600;
    font-size: 18px;
    padding-bottom: 11px;
  }

  /* Border that separates header and menu items */
  .break {
    background-color: #e5e5e5;
    border: 0;
    height: 2px;
    margin: 12px 0;
  }

  /* Custom classes for inputs */
  .big-input {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }
  .small-input {
    display: flex;
    flex-direction: column;
    margin-top: 25px;
    width: 115px;
  }

  /* Input and label defaults */
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
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
  input[type=number] {
    -moz-appearance: textfield;
  }

  /* Plus button */
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

  /* Options */
  .option-container {
    display: flex;
    flex-direction: column;
    margin-top: 25px;
    position: relative;
  }
  select {
    appearance: none;
    border: 2px solid #e5e5e5;
    padding: 3px 5px;
    border-radius: 5px;
    outline: none;
    margin-top: 5px;
  }
  .chevron-down {
    position: absolute;
    bottom: 4px;
    right: 10px;
    width: 15px;
    height: 15px;
  }
</style>
