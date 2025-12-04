<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue';

const preco = ref(0)
const descontoAplicado = ref(0)
const calculado10 = ref<boolean>(false)
const calculado20 = ref<boolean>(false)

function desc10() {
  descontoAplicado.value = 0.1
  calculado10.value = true
  calculado20.value = false
}
function desc20() {
  descontoAplicado.value = 0.2
  calculado20.value = true
  calculado10.value = false
}
function desc0() {
  descontoAplicado.value = 0
  calculado20.value = false
  calculado10.value = false
}

const precoFinal = computed(()=> {
  return preco.value - (preco.value*descontoAplicado.value)
})
</script>

<template>
  <header>
    <div>
      <p>Digite o preço do produto: </p>
      <input v-model.number="preco">

      <p>DESCONTOS</p>
      <div><button @click="desc10">10% de Desconto</button></div>
      <div><button @click="desc20">20% de Desconto</button></div>
      <div><button @click="desc0">Limpar Desconto</button></div>
    </div>
    <div v-if="calculado10">PREÇO FINAL: {{ precoFinal }} com 10% de desconto</div>
    <div v-if="calculado20">PREÇO FINAL: {{ precoFinal }} com 20% de desconto</div>
    <div v-if="calculado10 == false && calculado20 == false">Nenhum desconto aplicado</div>
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
