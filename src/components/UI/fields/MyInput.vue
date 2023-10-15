<script setup>
import debounce from "lodash.debounce";
import FieldWrapper from "@/components/UI/fields/FieldWrapper.vue";

const { modelValue } = defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue", "setTheme"]);

const handleInput = debounce((event) => {
  const inputValue = event.target.value;
  emit("update:modelValue", inputValue);

  if (inputValue.includes("zsu")) {
    emit("setTheme", "secondary");
  } else {
    emit("setTheme", "default");
  }
}, 500);
</script>

<template>
  <field-wrapper>
    <template #label/>
    <input :value="modelValue" @input="handleInput" placeholder="Enter 'zsu'" />
    <template #error/>
    <template #helper-text/>
  </field-wrapper>
</template>

<style scoped>

</style>