<template>
  
  <div class="calculator-container h-screen flex justify-center items-center">
    <div class="calculator bg-gray-800 p-16 rounded-lg shadow-md">
      <div class="display text-white text-4xl mb-8">{{ display }}</div>

      <div class="buttons grid grid-cols-4 gap-4">
        <button @click="appendToDisplay('7')" class="button text-3xl">7</button>
        <button @click="appendToDisplay('8')" class="button text-3xl">8</button>
        <button @click="appendToDisplay('9')" class="button text-3xl">9</button>
        <button @click="appendToDisplay('/')" class="button text-3xl">/</button>

        <button @click="appendToDisplay('4')" class="button text-3xl">4</button>
        <button @click="appendToDisplay('5')" class="button text-3xl">5</button>
        <button @click="appendToDisplay('6')" class="button text-3xl">6</button>
        <button @click="appendToDisplay('*')" class="button text-3xl">*</button>

        <button @click="appendToDisplay('1')" class="button text-3xl">1</button>
        <button @click="appendToDisplay('2')" class="button text-3xl">2</button>
        <button @click="appendToDisplay('3')" class="button text-3xl">3</button>
        <button @click="appendToDisplay('-')" class="button text-3xl">-</button>

        <button @click="appendToDisplay('0')" class="bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 button text-3xl">0</button>


        <button @click="appendToDisplay('.')" class="button text-3xl">.</button>
        <button @click="calculateResult()" class="button text-3xl">=</button>
        <button @click="appendToDisplay('+')" class="button text-3xl">+</button>

        <button class="clear col-span-2 text-3xl" @click="clearDisplay">C</button>
        
      </div>
    </div>
  </div>
</template>

<script>
import '../styles.css';


export default {
  data() {
    return {
      display: '0',
      expression: '',
    };
  },
  methods: {
    appendToDisplay(value) {
      if (this.display === '0') {
        this.display = value;
      } else {
        this.display += value;
      }
    },
    clearDisplay() {
      this.display = '0';
      this.expression = '';
    },
    calculateResult() {
      try {
        this.expression = this.display;
        this.display = eval(this.expression).toString();
      } catch (error) {
        this.display = 'Error';
      }
    },
  },
};
</script>





