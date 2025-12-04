<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue';

const valorProduto = ref(0)
const desconto = ref(0)

const CalcDesconto = computed (() => {
  return valorProduto.value - (valorProduto.value *(desconto.value/100))
})
</script>

<template>
  <header>
    <div>
      <h1>CALCULADORA DE DESCONTOS</h1>
      <p>Valor do produto(R$)</p>
      <input v-model.number="valorProduto">
      <br>
      <p>Valor do desconto (em %)</p>
      <input v-model.number="desconto">

      <p>Valor final do produto = R$ {{ CalcDesconto }}</p>
      <br>

      <div v-if="desconto < 5">DESCONTO PEQUENO</div>
      <div v-if="desconto >= 5 && desconto <= 10">DESCONTO MODERADO</div>
      <div v-if="desconto > 10">DESCONTO ALTO</div>
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
