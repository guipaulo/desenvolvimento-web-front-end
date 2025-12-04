<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue';

const clicks = ref(0)
function incrementar() {
  if (clicks.value < 10) {
    clicks.value++
  }
}
const tipo = computed(() => {
  if (clicks.value%2==0) return 'par'
  else return 'impar'
})

</script>

<template>
  <main>
    <div><button @click="incrementar">Clique aqui</button></div>
    <div>Numero de clicks: {{ clicks }}
      <span>{{ tipo }}</span>
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
