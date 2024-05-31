<script setup lang="ts">
import { ref } from 'vue'
import PictureComponent from './PictureComponent.vue'

const isWorking = ref(true)
const showEmail = ref(true)
const email = 'Valentim@email.vale'
const myLink = 'https://google.com'
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
    <p>Para acessar meu portfólio <a v-bind:href="myLink">basta clicar aqui</a></p>
    <PictureComponent />
  </div>
</template>

<style scoped lang="scss"></style>
