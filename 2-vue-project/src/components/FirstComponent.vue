<script setup lang="ts">
import MultipleEvents from './MultipleEvents.vue'
import ReusableComponent from './ReusableComponent.vue'

const name = 'Valentim'
const job = 'Software Developer'
</script>

<template>
  <section>
    <h1>I'm {{ name }}! My job is {{ job }}.</h1>
    <MultipleEvents />
    <ReusableComponent />
    <ReusableComponent />
  </section>
</template>

<style lang="scss"></style>
