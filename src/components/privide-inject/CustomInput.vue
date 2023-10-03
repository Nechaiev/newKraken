<template>
    <wrapper-custom-input :helperText="helperText" :error="error" :label="label">
        <input
            :type="type"
            :placeholder="placeholder"
            class="peer block min-h-[auto] w-full rounded ring-1 bg-transparent px-3 py-[0.32rem]"
            v-model="innerValue"
        />
    </wrapper-custom-input>
</template>

<script setup>
import WrapperCustomInput from "@/components/privide-inject/WrapperCustomInput.vue";
import { computed, inject } from "vue";

const form = inject("formData");

defineEmits(["update:modelValue"]);

const props = defineProps({
  placeholder: String,
  label: String,
  error: String,
  helperText: String,
  modelValue: String,
  type: {
    type: String,
    default: "text",
  },
  name: String,
});
const innerValue = computed({
  get() {
    return form.value[props.name];
  },
  set(val) {
    form.value[props.name] = val;
  },
});
</script>


