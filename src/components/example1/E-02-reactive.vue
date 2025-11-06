<template>
  <div>{{ fullName }}</div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';

const firstName = ref("Kyungsu");
const lastName = ref("Lee");

const fullName = computed(() => {
  return firstName.value + " " + lastName.value;
});

onMounted(() => {
  setTimeout(() => {
    firstName.value = "KSL";
  }, 2000);
});
</script>