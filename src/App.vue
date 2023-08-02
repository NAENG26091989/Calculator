<template>
  <div class="calculator">
    <input type="text" v-model="display" readonly  />
    <div class="buttons">
      <button v-for="button in buttons" :key="button.value" @click="handleClick(button.value)">
        {{ button.label }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      display: '',
      buttons: [
        { label: '7', value: '7' },
        { label: '8', value: '8' },
        { label: '9', value: '9' },
        { label: '4', value: '4' },
        { label: '5', value: '5' },
        { label: '6', value: '6' },
        { label: '1', value: '1' },
        { label: '2', value: '2' },
        { label: '3', value: '3' },
        { label: '0', value: '0' },
        { label: '+', value: '+' },
        { label: '-', value: '-' },
        { label: '*', value: '*' },
        { label: '/', value: '/' },
        { label: '=', value: 'equal' },
        { label: 'C', value: 'clear' },
      ],
    };
  },
  methods: {
    handleClick(value) {
      if (value === 'equal') {
        this.calculate();
      } else if (value === 'clear') {
        this.clearDisplay();
      } else {
        this.display += value;
      }
    },
    calculate() {
      try {
        this.display = eval(this.display);
      } catch (error) {
        this.display = 'Error';
      }
    },
    clearDisplay() {
      this.display = '';
    },
  },
};
</script>

<style>
.calculator {
  width: 400px;
  margin: 0 auto;
  margin-top: 2%;
  padding: 10px;
  border: 10px solid #ccc;
  box-shadow: 5px 5px 10px 10px rgba(0, 0, 0, 0.5);

  border-radius: 5px;
  background: orange;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 5px;
  margin-top: 10px;
}

button {
  padding:8px 20px;
  font-size: 30px;
  text-align: center;
}
input{
  width: 100%;
  height: 100px;
  font-size: 60px;
  font-weight: bold;
  color: red;
  border: 2px solid black;
}
</style>
