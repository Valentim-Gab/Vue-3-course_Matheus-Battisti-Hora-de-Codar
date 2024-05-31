<script setup lang="ts">
import { reactive } from 'vue'
import BtnSubmit from './form/BtnSubmit.vue'

const form = reactive({
  name: '',
  email: ''
})

function handleSubmit(event: Event) {
  event.preventDefault()

  console.log(form)
}
</script>

<template>
  <form @submit="handleSubmit">
    <!-- <InputText />
    <InputText /> -->
    <label for="name">Nome:</label>
    <input type="text" name="name" id="name" v-model="form.name" />
    <label for="email">E-mail:</label>
    <input type="email" name="email" id="email" v-model="form.email" />
    <BtnSubmit />
  </form>
</template>

<style scoped lang="scss">
form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
