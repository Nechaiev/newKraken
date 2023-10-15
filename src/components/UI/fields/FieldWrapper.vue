<script setup>
const props = defineProps({
  label: String,
  error: String,
  helperText: String,
});
</script>

<template>
  <div class="mb-5">
    <label class="font-bold" v-if="label">{{ label }}</label>
    <slot></slot>
    <slot name="error" v-if="error">{{ error }}</slot>
    <slot name="helper-text" v-if="helperText">{{ helperText }}</slot>
  </div>
</template>

<style scoped>

</style>