<script setup lang="ts">
import FirstComponent from '@/components/FirstComponent.vue'

const test = 'Parece que funcionou'
</script>

<template>
  <main>
    <FirstComponent />
    <p>Testando valor: {{ test }}</p>
  </main>
</template>
