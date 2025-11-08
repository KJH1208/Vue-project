<!-- ChildComponent.vue -->
<template>
  <div>
    <p>{{ message }}</p>
    <button @click="emit('custom-event', 'Hello from child')">Send Event</button>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  message: string;
}>();

const emit = defineEmits<{
  'custom-event': [payload: string];
}>();
</script>