<script setup lang="ts">
defineProps<{ msg: string | null }>()
</script>

<template>
  <div class="message-container">
    <p>{{ msg }}</p>
  </div>
</template>

<style scoped lang="scss">
.message-container {
  color: var(--color-dark-blue);
  background-color: var(--color-gray);
  border: 2px solid var(--color-blue-soft);
  border-radius: 0.25rem;
  padding: 0.75rem;
  max-width: 400px;
  margin: 2rem auto;
}
</style>
