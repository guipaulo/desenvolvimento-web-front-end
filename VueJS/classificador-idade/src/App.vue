<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue';

const idade = ref(0)
const isNotNumber = computed (() => {
  return typeof idade.value !== "number"
})

</script>

<template>
  <header>
    <div>
      <p>Digite uma idade: </p>
      <input v-model.number="idade">
      <br>
      <p v-if="isNotNumber">Digite uma idade válida!</p>

      <p v-if="idade < 12">A pessoa é uma criança</p>
      <p v-if="idade >= 12 && idade <=17 ">A pessoa é um adolescente</p>
      <p v-if="idade >= 18 && idade <= 59">A pessoa é um adulto</p>
      <p v-if="idade >= 60">A pessoa é um idoso</p>
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
