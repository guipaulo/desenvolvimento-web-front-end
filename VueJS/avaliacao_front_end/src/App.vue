<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue';

const inicio_jogo = ref<boolean>(false)
const clicksJog1 = ref(0)
const clicksJog2 = ref(0)

function aumentarpontos1() {
  if (clicksJog1.value >= 0) {
    clicksJog1.value++
    inicio_jogo.value = true
  }
}
function aumentarpontos2() {
  if (clicksJog2.value >= 0) {
    clicksJog2.value++
    inicio_jogo.value = true
  }
}

function diminuirpontos1() {
  if (clicksJog1.value > 0) {
    clicksJog1.value--
  }
}
function diminuirpontos2() {
  if (clicksJog2.value > 0) {
    clicksJog2.value--
  }
}

const ganhador = computed(() => {
  if (clicksJog2.value == clicksJog1.value) return 'O jogo está empatado'
  if (clicksJog1.value > clicksJog2.value) return 'O jogador 1 está ganhando'
  if (clicksJog2.value > clicksJog1.value) return 'O jogador 2 está ganhando'

})


</script>

<template>
  <main>
    <div class="color">
    <div class="container">
      <h1>PLACAR INTERATIVO - JOGO COM VUEJS </h1>
    </div>
    <br>
    <div class="container" v-if="!inicio_jogo">AGUARDANDO INICIO DO JOGO</div>
    <div class="container-flex">
      <button @click="aumentarpontos1" style="color: green">+1 ponto - Jogador 1</button>
      <br>
      <button @click="aumentarpontos2" style="color: green">+1 ponto - Jogador 2</button>
    </div>
    <div class="container-flex">
      <button @click="diminuirpontos1" style="color: red;">-1 ponto - Jogador 1</button>
      <br>
      <button @click="diminuirpontos2" style="color: red;"> -1 ponto - Jogador 2</button>
    </div>

    <div class="container-flex">
      JOGADOR 1: {{ clicksJog1 }}
    </div>
    <div class="container-flex">
      JOGADOR 2: {{ clicksJog2 }}
    </div>
    <div class="container-flex">
      <span>{{ ganhador }}</span>
    </div>
    </div>
  </main>
</template>

<style scoped>
.color{
  background-color: aliceblue;
}
.container-flex{
  display:flex;
  justify-content: space-around;
  background-color: aliceblue;
}

.container {
  background-color: #ADD8E6;
  text-align: center;
  font-weight: bold;
}

header {
  line-height: 1.5;

}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;

  }
}
</style>
