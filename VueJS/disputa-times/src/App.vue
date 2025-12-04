<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue';

const clicks1 = ref(0)
const clicks2 = ref(0)
const inicio = ref<boolean>(false)

function incrementar1() {
  if (clicks1.value >= 0) {
    clicks1.value++
    inicio.value = true
  }
}
function incrementar2() {
  if (clicks2.value >= 0) {
    clicks2.value++
    inicio.value = true
  }
}

function decrementar1() {
  if (clicks1.value > 0) {
    clicks1.value--
  }
}
function decrementar2() {
  if (clicks2.value > 0) {
    clicks2.value--
  }
}

const ganhador = computed(() => {
  if (clicks1.value > clicks2.value) return 'Jogador 1 na frente'
  if (clicks2.value > clicks1.value) return 'Jogador 2 na frente'
  if (clicks2.value == clicks1.value) return 'Jogo empatado'
})

//const iniciojogo = computed(() => {
//if (clicks1.value == 0 && clicks2.value == 0) return 'O JOGO AINDA NÃO COMEÇOU'
//})
//<span>{{ iniciojogo }}</span>


</script>

<template>
  <main>
    <div>
      <h3>DISPUTA DE TIMES</h3>
    </div>
    <br>
    <div><button @click="incrementar1">Aumentar Pontos Jogador 1</button> <button @click="incrementar2">Aumentar Pontos
        Jogador 2</button></div>
    <div><button @click="decrementar1">Diminuir Pontos Jogador 1</button> <button @click="decrementar2">Diminuir Pontos
        Jogador 2</button></div>
    <div v-if="!inicio">O JOGO AINDA NÃO COMEÇOU</div>
    <div>JOGADOR 1: {{ clicks1 }}
      <hr>
      JOGADOR 2: {{ clicks2 }}
      <br>
      <span>{{ ganhador }}</span>
    </div>
  </main>
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
