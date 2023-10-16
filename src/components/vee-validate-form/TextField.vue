<template>
  <validation-field :label="label" :errors="errors">
    <input
      :name="name"
      :type="type"
      :placeholder="placeholder"
      :class="fieldClasses"
      v-model="innerValue"
    />
  </validation-field>
</template>

<script setup>
import ValidationField from "@/components/vee-validate-form/ValidationField.vue";
import { useField } from "vee-validate";

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    default: "text",
  },
  label: String,
  placeholder: String,
  mask: String,
});

const { value: innerValue, errors } = useField(() => props.name);

const fieldClasses =
  "peer block min-h-[auto] w-full rounded ring-1 bg-transparent px-3 py-[0.32rem] leading-[1.6] placeholder-black::placeholder outline-none transition-all duration-200 ease-linear motion-reduce:transition-none";
</script>