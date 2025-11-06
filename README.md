# vue-demo

## Vue3 Migration Complete! 🎉

This project has been successfully migrated from Vue2 to Vue3 using Composition API with `<script setup>` syntax.

---

## 📋 Migration Summary

### 🔄 Converted Components (12 files)

All components have been refactored from **Options API** to **Composition API** (`<script setup lang="ts">`).

#### **Example 1: Basic Concepts** (3 files)
- `E-01-instance.vue` - Basic data binding with `ref()`
- `E-02-instance.vue` - Computed properties and lifecycle hooks
- `E-03-instance.vue` - Two-way binding with `v-model`

#### **Example 2: Directives** (1 file)
- `E-04-directives.vue` - Vue directives (v-if, v-for, v-show, v-bind, v-on, etc.)

#### **Example 3: Component Communication** (2 files)
- `ChildComponent.vue` - Props and emits with TypeScript types
- `ParentComponent.vue` - Parent-child communication

#### **Example 4: Provide/Inject** (3 files)
- `ChildComponent1.vue` - Inject shared data
- `ChildComponent2.vue` - Nested inject
- `ParentComponent.vue` - Provide shared data

#### **Example 5: API Comparison** (3 files)
- `E-07-Options-API.vue` - Options API converted to Composition API
- `E-08-composition-api.vue` - Composition API with `setup()` converted to `<script setup>`
- `E-09-composition-API2.vue` - Already using `<script setup>`, added TypeScript types

#### **Example 6: Reactivity System** (3 files)
- `E-10-ref.vue` - Using `ref()` for primitive values
- `E-11-reactive.vue` - Using `reactive()` for objects
- `E-12-ref-component.vue` - Template refs for DOM elements

---

## 🔑 Key Changes

### **1. Script Block Structure**

**Before (Vue2 Options API):**
```vue
<script>
export default {
  data() {
    return { count: 0 }
  },
  methods: {
    increment() { this.count++ }
  }
}
</script>
```

**After (Vue3 Composition API):**
```vue
<script setup lang="ts">
import { ref } from 'vue';

const count = ref(0);
const increment = () => { count.value++ };
</script>
```

---

### **2. Reactivity**

| Feature | Vue2 | Vue3 |
|---------|------|------|
| Data | `data() { return {...} }` | `ref()` or `reactive()` |
| Computed | `computed: { ... }` | `computed(() => ...)` |
| Methods | `methods: { ... }` | `const funcName = () => {...}` |
| Watch | `watch: { ... }` | `watch(source, callback)` |

---

### **3. Lifecycle Hooks**

| Vue2 Options API | Vue3 Composition API |
|------------------|----------------------|
| `beforeCreate()` | `setup()` (직접 실행) |
| `created()` | `setup()` (직접 실행) |
| `beforeMount()` | `onBeforeMount()` |
| `mounted()` | `onMounted()` |
| `beforeUpdate()` | `onBeforeUpdate()` |
| `updated()` | `onUpdated()` |
| `beforeUnmount()` | `onBeforeUnmount()` |
| `unmounted()` | `onUnmounted()` |

---

### **4. Props & Emits**

**Before:**
```vue
<script>
export default {
  props: ['message'],
  methods: {
    sendEvent() {
      this.$emit('custom-event', payload)
    }
  }
}
</script>
```

**After:**
```vue
<script setup lang="ts">
defineProps<{ message: string }>();

const emit = defineEmits<{
  'custom-event': [payload: string];
}>();

const sendEvent = () => {
  emit('custom-event', payload);
};
</script>
```

---

### **5. Provide/Inject**

**Before:**
```vue
<script>
export default {
  provide() {
    return { key: 'value' }
  },
  inject: ['key']
}
</script>
```

**After:**
```vue
<script setup lang="ts">
import { provide, inject } from 'vue';

// Provide
provide('key', 'value');

// Inject
const key = inject<string>('key');
</script>
```

---

### **6. Template Refs**

**Before:**
```vue
<script>
export default {
  mounted() {
    this.$refs.inputField.focus();
  }
}
</script>
```

**After:**
```vue
<script setup lang="ts">
import { ref, onMounted } from 'vue';

const inputField = ref<HTMLInputElement | null>(null);

onMounted(() => {
  inputField.value?.focus();
});
</script>

<template>
  <input ref="inputField" />
</template>
```

---

## ✅ Configuration Files Status

All configuration files are already Vue3-compatible:

- ✅ `main.ts` - Using `createApp()` (Vue3)
- ✅ `App.vue` - Using `defineComponent` (Vue3)
- ✅ `package.json` - Vue 3.2.13 installed
- ✅ `shims-vue.d.ts` - Using `DefineComponent` type
- ✅ `tsconfig.json` - Optimized for Vue3

**No additional configuration changes needed!**

---

## 🚀 Project Setup

### Install dependencies
```bash
npm install
```

### Compiles and hot-reloads for development
```bash
npm run serve
```

### Compiles and minifies for production
```bash
npm run build
```

### Lints and fixes files
```bash
npm run lint
```

---

## 📚 Additional Resources

- [Vue 3 Official Documentation](https://vuejs.org/)
- [Composition API Guide](https://vuejs.org/guide/extras/composition-api-faq.html)
- [Script Setup Documentation](https://vuejs.org/api/sfc-script-setup.html)
- [Vue 3 Migration Guide](https://v3-migration.vuejs.org/)
- [TypeScript with Vue](https://vuejs.org/guide/typescript/overview.html)

---

## 🎯 Benefits of Vue3 Composition API

1. **Better TypeScript Support** - Full type inference
2. **Better Code Organization** - Logical concerns grouped together
3. **Better Code Reuse** - Composable functions
4. **Smaller Bundle Size** - Tree-shaking friendly
5. **Better Performance** - Optimized reactivity system

---

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).