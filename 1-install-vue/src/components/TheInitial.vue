<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  name: '',
  email: ''
})

const name = ref('')

function submitForm(event: Event) {
  event.preventDefault()

  name.value = form.value.name

  console.log(form.value)
}
</script>

<template>
  <section>
    <form id="app-form" @submit.prevent="submitForm" class="main-form">
      <input type="text" name="name" id="name" v-model="form.name" placeholder="Digite seu nome" />
      <input
        type="email"
        name="email"
        id="email"
        v-model="form.email"
        placeholder="Digite seu email"
      />
      <button type="submit">Enviar</button>
    </form>
    <p>O seu nome é: {{ name }}</p>
  </section>
</template>

<style scoped lang="scss">
.main-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  gap: 0.5rem;
}
</style>
