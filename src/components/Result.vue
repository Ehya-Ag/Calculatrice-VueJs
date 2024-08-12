<template>
  <div class="result mt-3">
    <div v-if="result !== null" class="alert alert-success" role="alert">
      Résultat : {{ result }}
    </div>
    <div v-if="errorMessage !== ''" class="alert alert-danger" role="alert">
      {{ errorMessage }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Result',
  props: {
    result: {
      type: Number,
      default: null
    },
    errorMessage: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>
/* Ajoutez ici les styles spécifiques au composant Result.vue si nécessaire */
</style>
