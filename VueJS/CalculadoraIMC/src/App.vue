<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue'

const peso = ref()
const altura = ref()


const calculadoraIMC = computed(() => {
  return (peso.value/(altura.value*altura.value))
})
</script>

<template>
<div>Peso</div>
<div>Altura</div>
<input v-model="peso"/>
<input v-model="altura"/>

<div v-if="calculadoraIMC < 18.5">Abaixo do Peso</div>
<div v-if="calculadoraIMC >= 18.5 && calculadoraIMC < 25">Peso normal</div>
<div v-if="calculadoraIMC >= 25 && calculadoraIMC < 30">Sobrepeso</div>
<div v-if="calculadoraIMC >= 30">Obesidade</div>

<div>Seu imc é {{ calculadoraIMC }}</div>


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
