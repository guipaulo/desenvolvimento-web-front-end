<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue'

const real = ref(0)

const ConversorDolar = computed(()=> {
  return real.value / 5.36
})

const ConversorEuro = computed(()=> {
  return real.value / 6.22
})
</script>

<template>
  <header>
    <div>
      <h1>CONVERSOR DE MOEDAS</h1>
      <p>Valor em Reais:</p>
      <input v-model.number="real">
      <br>
      <p>Valor em Dolares: {{ ConversorDolar.toFixed(2) }}</p>
      <br>
      <p>Valor em Euros: {{ ConversorEuro.toFixed(2)}}</p>
      <br>
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
