<template>
  <div
    class="input-wrapper relative max-w-screen-md w-full mx-auto p-4 mb-4 border-2 rounded-[4px]"
  >
    <validation-field :label="label" :errors="errors">
      <input
        :name="name"
        :type="type"
        v-model="innerValue"
        :value="value"
        class="m-4"
      />
    </validation-field>
  </div>
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
    default: "radio",
    validator(value) {
      return ["radio", "checkbox"].includes(value);
    },
  },
  value: null,
  label: String,
});
const { value: innerValue, errors } = useField(() => props.name, undefined, {
  type: props.type,
  checkedValue: () => props.value,
});
</script>

<style scoped></style>
