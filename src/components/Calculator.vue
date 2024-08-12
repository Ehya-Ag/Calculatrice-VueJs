<template>
  <div class="calculator">
    <div class="mb-5">
      <label class="form-label">Opération :</label>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="addition" value="addition" v-model="selectedOperation">
        <label class="form-check-label" for="addition">Addition</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="multiplication" value="multiplication" v-model="selectedOperation">
        <label class="form-check-label" for="multiplication">Multiplication</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="division" value="division" v-model="selectedOperation">
        <label class="form-check-label" for="division">Division</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="subtraction" value="subtraction" v-model="selectedOperation">
        <label class="form-check-label" for="subtraction">Soustraction</label>
      </div>
    </div>
    
    <div class="mb-3">
      <label class="form-label">Première valeur :</label>
      <input type="number" class="form-control" v-model.number="value1">
    </div>
    
    <div class="mb-3">
      <label class="form-label">Deuxième valeur :</label>
      <input type="number" class="form-control" v-model.number="value2">
    </div>
    
    <button class="btn btn-primary" @click="calculate">Calculer</button>
    
    <Result :result="result" :errorMessage="errorMessage" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Result from './Result.vue';

const selectedOperation = ref('addition');
const value1 = ref(0);
const value2 = ref(0);
const result = ref(null);
const errorMessage = ref('');

const calculate = () => {
  errorMessage.value = '';

  switch (selectedOperation.value) {
    case 'addition':
      result.value = parseFloat(value1.value) + parseFloat(value2.value);
      break;
    case 'multiplication':
      result.value = parseFloat(value1.value) * parseFloat(value2.value);
      break;
    case 'division':
      if (parseFloat(value2.value) === 0) {
        errorMessage.value = "Division par zéro est impossible.";
        result.value = null;
      } else {
        result.value = parseFloat(value1.value) / parseFloat(value2.value);
      }
      break;
    case 'subtraction':
      result.value = parseFloat(value1.value) - parseFloat(value2.value);
      break;
    default:
      result.value = null;
  }
};
</script>

<style scoped>
</style>

