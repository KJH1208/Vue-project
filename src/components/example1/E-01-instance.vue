<template>
  <div>Hello, {{ message }}</div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const message = ref("Vue!");
</script>

<style scoped>
div {
  color: blue;
}
</style>