<script setup lang="ts">
import { onBeforeMount, onMounted, ref } from 'vue'

const name = ref('Ainda não definido')

function printLifeCycle() {
  console.log('Executou!')
}

printLifeCycle() // onCreated

onBeforeMount(() => {
  setTimeout(() => {
    name.value = 'Valentim'

    printLifeCycle()
  }, 1000)
}),
  onMounted(() => {
    setTimeout(() => {
      name.value = 'Rodrigo'

      printLifeCycle()
    }, 2000)
  })
</script>

<template>
  <section>
    <h2>Meu nome é? {{ name }}</h2>
  </section>
</template>

<style lang="scss"></style>
