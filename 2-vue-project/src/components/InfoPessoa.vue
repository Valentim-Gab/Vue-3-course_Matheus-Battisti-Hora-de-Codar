<script setup lang="ts">
import { computed, reactive, ref, defineProps } from 'vue'
import PictureComponent from './PictureComponent.vue'

const props = defineProps<{ email: string; isWorking: boolean }>()

interface User {
  isWorking: boolean
  email: string
  myLink: string
  backendTechnologies: string[]
  frontendTechnologies: { id: number; name: string }[]
}

const user: User = reactive<User>({
  isWorking: props.isWorking,
  email: props.email,
  myLink: '/projetos',
  backendTechnologies: ['Java', 'TypeScript', 'Delphi'],
  frontendTechnologies: [
    {
      id: 1,
      name: 'Vue'
    },
    {
      id: 2,
      name: 'React'
    },
    {
      id: 3,
      name: 'Angular'
    }
  ]
})

const isShowingEmail = ref(true)
const btnText = computed(() => (isShowingEmail.value ? 'Esconder email' : 'Mostrar email'))

function showEmail() {
  isShowingEmail.value = !isShowingEmail.value
}
</script>

<template>
  <div>
    <p v-if="user.isWorking">Estou trabalhando no presencial.</p>
    <p v-else>Estou em busca de novas oportunidades!</p>
    <p>Utilizo as seguintes tecnologias para Back-end:</p>
    <ul>
      <li v-for="(technology, index) in user.backendTechnologies" :key="index">
        {{ technology }}
      </li>
    </ul>
    <p>Utilizo as seguintes tecnologias para Front-end:</p>
    <ul>
      <li v-for="technology in user.frontendTechnologies" :key="technology.id">
        {{ technology.name }}
      </li>
    </ul>
    <div>
      <button @click="showEmail">{{ btnText }}</button>
    </div>
    <p v-show="isShowingEmail">Mande uma mensagem para: {{ user.email }}</p>
    <p>Para acessar meu portfólio <a v-bind:href="user.myLink">basta clicar aqui</a></p>
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
