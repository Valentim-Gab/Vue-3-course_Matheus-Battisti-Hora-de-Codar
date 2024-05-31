<script setup lang="ts">
import { computed, ref } from 'vue'
import PictureComponent from './PictureComponent.vue'

const isWorking = ref(true)
const isShowingEmail = ref(true)
const email = 'Valentim@email.vale'
const myLink = 'https://google.com'
const btnText = computed(() => (isShowingEmail.value ? 'Esconder email' : 'Mostrar email'))

function showEmail() {
  isShowingEmail.value = !isShowingEmail.value
}
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
    <div>
      <button @click="showEmail">{{ btnText }}</button>
    </div>
    <p v-show="isShowingEmail">Mande uma mensagem para: {{ email }}</p>
    <p>Para acessar meu portfólio <a v-bind:href="myLink">basta clicar aqui</a></p>
    <PictureComponent />
  </div>
</template>

<style scoped lang="scss">
button {
  background-color: hsla(160, 100%, 37%, 0.2);
  border: none;
  border-radius: 0.5rem;
  color: white;
  padding: 1rem 2rem;
  text-align: center;
  font-size: 16px;
  margin: 1rem 0;
  cursor: pointer;
  transition: background-color 0.2s;

  &:hover {
    background-color: hsla(160, 100%, 37%, 0.4);
  }
}

ul {
  margin-left: 2rem;
}
</style>
