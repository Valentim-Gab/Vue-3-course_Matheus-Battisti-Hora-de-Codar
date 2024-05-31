<script setup lang="ts">
import InfoPessoa from './InfoPessoa.vue'
import { ref } from 'vue'

const name = ref('Valentim')
</script>

<template>
  <section>
    <h2>Esta é a descrição da pessoa: {{ name }}</h2>
    <InfoPessoa />
  </section>
</template>

<style scoped lang="scss"></style>
