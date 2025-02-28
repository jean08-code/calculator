<script setup>
import { ref } from 'vue';

const input = ref('');
const result = ref('');

const append = (value) => {
  input.value += value;
};

const clearInput = () => {
  input.value = '';
  result.value = '';
};

const calculate = () => {
  try {
    result.value = eval(input.value);
  } catch (error) {
    result.value = 'Error';
  }
};
</script>

<template>
  <div class="calculator">
    <div class="display">
      <div class="input">{{ input }}</div>
      <div class="result">{{ result }}</div>
    </div>
    <div class="buttons">
      <button @click="append('7')">7</button>
      <button @click="append('8')">8</button>
      <button @click="append('9')">9</button>
      <button class="operator" @click="append('/')">/</button>
      <button @click="append('4')">4</button>
      <button @click="append('5')">5</button>
      <button @click="append('6')">6</button>
      <button class="operator" @click="append('*')">*</button>
      <button @click="append('1')">1</button>
      <button @click="append('2')">2</button>
      <button @click="append('3')">3</button>
      <button class="operator" @click="append('-')">-</button>
      <button @click="append('0')">0</button>
      <button class="equal" @click="calculate">=</button>
      <button @click="append('.')">.</button>
      <button class="operator" @click="append('+')">+</button>
      <button class="clear" @click="clearInput">C</button>
    </div>
  </div>
</template>

<style scoped>
.calculator {
  width: 250px;
  margin: auto;
  padding: 15px;
  border-radius: 10px;
  background: #ddfcdc;
  text-align: center;
}

.display {
  background: #cdccf0;
  padding: 10px;
  font-size: 24px;
  border-radius: 5px;
  margin-bottom: 10px;
}

.input {
  min-height: 30px;
}

.result {
  font-size: 18px;
  color: #2600ff;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 5px;
}

button {
  padding: 15px;
  font-size: 18px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
  background: #5340ff;
  color: white;
}

button.operator {
  background: #fc7979;
}

button.equal {
  background: #78afee;
}

button.clear {
  background: #dc3545;
  grid-column: span 4;
}

button:hover {
  opacity: 0.8;
}
</style>