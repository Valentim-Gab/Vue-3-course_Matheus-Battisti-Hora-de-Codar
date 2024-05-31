<script setup lang="ts">
import { onBeforeMount, onMounted, ref } from 'vue'

const name = ref('Ainda não definido')

onBeforeMount(() => {
  setTimeout(() => {
    name.value = 'Valentim'
  }, 1000)
}),

onMounted(() => {
  setTimeout(() => {
    name.value = 'Rodrigo'
  }, 2000)
})
</script>

<template>
  <section>
    <h2>Meu nome é? {{ name }}</h2>
  </section>
</template>

<style lang="scss"></style>
