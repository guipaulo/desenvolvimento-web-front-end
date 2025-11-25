<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue'
const celsius = ref(0)

const GrausKelvin = computed(() => {
  return +celsius.value +273.15
})

const GrausFahrenheit = computed(() => {
  return (celsius.value * 9 / 5) + 32
})
</script>

<template>
  <header>
    <div>
      <h1>CONVERSOR DE TEMPERATURA</h1>
      <p>Temperatura em Celsius</p>
      <input v-model="celsius">
      <p>Temperatura em Celsius = {{ celsius }}</p>
      <p>Temperatura em Kelvin = {{ GrausKelvin }}</p>
      <p>Temperatura em Fahrenheit = {{ GrausFahrenheit }}</p>
    </div>

    <div v-if="celsius < 0">Água estaria congelada nessa temperatura.</div>
    <div v-if="celsius >= 0 && celsius < 100">Temperatura comum no dia a dia.</div>
    <div v-if="celsius >= 100">Água entraria em ebulição nessa temperatura.</div>
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
