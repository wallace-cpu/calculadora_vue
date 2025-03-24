<template>
  <div class="calculator">
    <div class="inputs">
      <input type="number" v-model.number="num1" placeholder="Número 1" />
      <select v-model="operation">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input type="number" v-model.number="num2" placeholder="Número 2" />
    </div>
    <div class="result">Resultado: {{ result }}</div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operation = ref('+');

const result = computed(() => {
  switch (operation.value) {
    case '+': return num1.value + num2.value;
    case '-': return num1.value - num2.value;
    case '*': return num1.value * num2.value;
    case '/': return num2.value !== 0 ? num1.value / num2.value : 'Erro';
    default: return 'Erro';
  }
});
</script>

<style scoped>
.calculator {
  width: 250px;
  margin: 20px auto;
  padding: 10px;
  background: #222;
  color: #fff;
  text-align: center;
  border-radius: 10px;
}

.inputs {
  display: flex;
  justify-content: center;
  gap: 5px;
  margin-bottom: 10px;
}

input, select {
  padding: 8px;
  font-size: 1em;
  border: none;
  border-radius: 5px;
}

.result {
  font-size: 1.5em;
  background: #444;
  padding: 10px;
  border-radius: 5px;
}
</style>
