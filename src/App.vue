<template>
  <div class="calculator">
    <div class="display">{{ current || '0' }}</div>
    <div class="buttons">
      <button @click="clear">C</button>
      <button @click="append('/')">/</button>
      <button @click="append('*')">*</button>
      <button @click="backspace">⌫</button>

      <button v-for="n in 9" :key="n" @click="append(n.toString())">{{ n }}</button>

      <button @click="append('-')">-</button>
      <button @click="append('0')">0</button>
      <button @click="append('.')">.</button>
      <button @click="append('+')">+</button>
      
      <button class="equal" @click="calculate">=</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const current = ref('');

const append = (value) => {
  current.value += value;
};

const clear = () => {
  current.value = '';
};

const backspace = () => {
  current.value = current.value.slice(0, -1);
};

const calculate = () => {
  try {
    current.value = eval(current.value).toString();
  } catch {
    current.value = 'Erro';
  }
};
</script>

<style scoped>
.calculator {
  width: 220px;
  margin: 20px auto;
  padding: 10px;
  background: #222;
  color: #fff;
  text-align: center;
  border-radius: 10px;
}

.display {
  font-size: 1.8em;
  padding: 10px;
  background: #444;
  margin-bottom: 10px;
  border-radius: 5px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 5px;
}

button {
  padding: 15px;
  font-size: 1.2em;
  border: none;
  cursor: pointer;
  background: #666;
  color: white;
  border-radius: 5px;
}

button:active {
  background: #888;
}

.equal {
  grid-column: span 4;
  background: #ff9800;
}
</style>
