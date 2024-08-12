<template>
  <div class="container">
    <h1 class="my-5">Calculatrice VueJS</h1>
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: {
    Calculator,
    Result
  }
}
</script>

<style>
</style>
