<script setup lang="ts">
import { ref } from 'vue'

const multipleEvents = ref('')

function first(txt: string) {
  multipleEvents.value = txt
}

function second(txt: string) {
  setTimeout(() => {
    multipleEvents.value = txt
  }, 1000)
}

function third() {
  setTimeout(() => {
    multipleEvents.value = ''
  }, 2000)
}
</script>

<template>
  <div>
    <button @click="first('Primeiro evento'), second('Segundo evento'), third()">
      Ativar múltiplos eventos
    </button>
    <p>{{ multipleEvents }}</p>
  </div>
</template>

<style scoped lang="scss">
div {
  margin: 4rem;
}
</style>
