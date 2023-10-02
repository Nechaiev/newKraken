<script setup>
import WrapperCustomInput from "@/components/WrapperCustomInput.vue";

defineEmits(
    ['update:modelValue', ]
)

defineProps({
  placeholder: String,
  label: String,
  error: String,
  helperText: String,
  modelValue: String,
  type:  {
    type: String,
    default: "text"
  },
  name: String,
})
</script>

<template>
  <wrapper-custom-input :helperText="helperText" :error="error" :label="label">
    <input :type="type"
           :placeholder="placeholder"
           class="peer block min-h-[auto] w-full rounded ring-1 bg-transparent px-3 py-[0.32rem]"
           @input="$emit('update:modelValue', $event.target.value)"
           :value="modelValue"
    >
  </wrapper-custom-input>
</template>