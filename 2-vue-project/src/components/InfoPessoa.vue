<script setup lang="ts">
import { ref } from 'vue';

const isWorking = ref(true)
const showEmail = ref(true)
const email = ref('Valentim@email.vale')
</script>

<template>
  <div>
    <p v-if="isWorking">Estou trabalhando no presencial.</p>
    <p v-else>Estou em busca de novas oportunidades!</p>
    <p>Utilizo as seguintes tecnologias:</p>
    <ul>
      <li>Vue</li>
      <li>TypeScript</li>
      <li>Delphi</li>
    </ul>
    <p v-show="showEmail">Mande uma mensagem para: {{ email }}</p>
  </div>
</template>

<style scoped lang="scss"></style>
