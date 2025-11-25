<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, computed } from 'vue'
const senha = ref('')

const ContadorLetras = computed(() => {
  return senha.value.length
})
</script>

<template>
  <header>
    <div>
      <h1>Verificador de Senha</h1>
      <p>Digite sua senha: </p>
      <input v-model="senha">
      <p>Sua senha possui {{ ContadorLetras }} caracteres</p>
      <p v-if="ContadorLetras < 5" class="fraca">Senha Fraca</p>
      <p v-if="ContadorLetras >= 5 && ContadorLetras <= 8" class="media">Senha Média</p>
      <p v-if="ContadorLetras > 8" class="forte">Senha Forte</p>
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

.fraca {
  background-color: rgb(131, 0, 0);
  color: white;
  text-align: center;
}
.media {
  background-color: rgb(255, 103, 48);
  color: white;
  text-align: center;
}

.forte {
  background-color: green;
  color: white;
  text-align: center;
}
</style>
