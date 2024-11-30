<script setup>
import fancyButton from './components/FancyButton.vue';
</script>

<template>
  <div class="content">
    <fancy-button>
      <template #icon="{ hover }">
        {{ hover ? '👻':'👾' }}</template>
        Hasme clic!
    </fancy-button>
  </div>
</template>

<style scoped>
</style>