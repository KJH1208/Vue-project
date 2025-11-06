<template>
  <div>{{ fullName }}</div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';

const firstName = ref("Juhyeon");
const lastName = ref("Kang");

const fullName = computed(() => {
  return firstName.value + " " + lastName.value;
});

onMounted(() => {
  setTimeout(() => {
    firstName.value = "KJH";
  }, 2000);
});
</script>