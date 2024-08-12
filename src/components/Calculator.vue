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
      <input type="number" class="form-control" v-model="value1">
    </div>
    
    <div class="mb-3">
      <label class="form-label">Deuxième valeur :</label>
      <input type="number" class="form-control" v-model="value2">
    </div>
    
    <button class="btn btn-primary" @click="calculate">Calculer</button>
    
    <Result :result="result" :errorMessage="errorMessage" />
  </div>
</template>

<script>
import Result from './Result.vue';

export default {
  name: 'Calculator',
  components: {
    Result
  },
  data() {
    return {
      selectedOperation: 'addition',
      value1: 0,
      value2: 0,
      result: null,
      errorMessage: ''
    };
  },
  methods: {
    calculate() {
      switch (this.selectedOperation) {
        case 'addition':
          this.result = parseFloat(this.value1) + parseFloat(this.value2);
          break;
        case 'multiplication':
          this.result = parseFloat(this.value1) * parseFloat(this.value2);
          break;
        case 'division':
          if (parseFloat(this.value2) === 0) {
            this.errorMessage = "Division par zéro est impossible.";
            this.result = null;
          } else {
            this.result = parseFloat(this.value1) / parseFloat(this.value2);
          }
          break;
        case 'subtraction':
          this.result = parseFloat(this.value1) - parseFloat(this.value2);
          break;
        default:
          this.result = null;
      }
    }
  }
}
</script>

<style scoped>
</style>
