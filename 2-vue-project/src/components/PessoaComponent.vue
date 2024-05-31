<script setup lang="ts">
import InfoPessoa from './InfoPessoa.vue'
import { ref } from 'vue'

const name = ref('Valentim')
const email = ref('Kenny@email.vale')
</script>

<template>
  <section>
    <h2>Esta é a descrição da pessoa: {{ name }}</h2>
    <InfoPessoa :email="email" :isWorking="false" />
  </section>
</template>

<style scoped lang="scss"></style>
