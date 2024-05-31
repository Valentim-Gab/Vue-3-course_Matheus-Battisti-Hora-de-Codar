<script setup lang="ts">
import FirstComponent from '@/components/FirstComponent.vue'
import LifeCycle from '@/components/LifeCycle.vue'

const test = 'Parece que funcionou'
</script>

<template>
  <main>
    <FirstComponent />
    <p>Testando valor: {{ test }}</p>
    <LifeCycle />
  </main>
</template>
