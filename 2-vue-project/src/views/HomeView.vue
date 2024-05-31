<script setup lang="ts">
import FirstComponent from '@/components/FirstComponent.vue'
import FormExample from '@/components/FormExample.vue'
import LifeCycle from '@/components/LifeCycle.vue'
import PessoaComponent from '@/components/PessoaComponent.vue'

const test = 'Parece que funcionou'
</script>

<template>
  <main>
    <FirstComponent />
    <hr />
    <p>Testando valor: {{ test }}</p>
    <hr />
    <LifeCycle />
    <hr />
    <PessoaComponent />
    <hr />
    <FormExample />
  </main>
</template>

<style scoped lang="scss">
hr {
  margin: 1rem 0;
}

main {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
</style>
