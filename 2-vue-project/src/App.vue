<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div>
    <header>
      <nav>
        <RouterLink to="/">Home</RouterLink>
      </nav>
    </header>
    <RouterView />
  </div>
</template>

<style scoped lang="scss"></style>
