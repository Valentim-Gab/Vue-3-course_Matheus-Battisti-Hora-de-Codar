<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <header class="header">
    <nav>
      <RouterLink to="/" class="header-link">Home</RouterLink>
      <RouterLink to="#" class="header-link">Projetos</RouterLink>
      <RouterLink to="#" class="header-link">Contato</RouterLink>
    </nav>
  </header>
</template>

<style scoped lang="scss">
.header {
  background-color: hsla(160, 100%, 37%, 0.4);

  nav {
    display: flex;

    .header-link {
      margin-right: 0.5rem;
      color: #ddd;
      transition: 0.5s;

      &:hover {
        color: #40e0d0;
      }
    }
  }
}
</style>
