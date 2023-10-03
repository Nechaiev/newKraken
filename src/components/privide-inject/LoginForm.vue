<template>
  <form
    @submit.prevent="onSubmit"
    class="max-w-lg mx-auto my-4 p-4 bg-white rounded-lg shadow-lg"
  >
    <pre>{{ form }}</pre>
    <custom-input
      name="login"
      v-model="form.login"
      :error="errors.login"
      label="Login"
      class="mb-2"
    />
    <custom-input
      v-model="form.password"
      :error="errors.password"
      label="Password"
      type="password"
      name="password"
      class="mb-2"
    />
    <button class="text-black border-black rounded p-2 border-solid border-2">
      Submit
    </button>
  </form>
</template>

<script setup>
import { provide, ref } from "vue";
import CustomInput from "@/components/privide-inject/CustomInput.vue";

const form = ref({
  login: "",
  password: "",
});
const errors = ref({
  login: "",
  password: "",
});
const onSubmit = () => {
  console.log(form.value);
  const validationErrors = validateForm(form.value);
  Object.assign(errors.value, validationErrors);

  if (!Object.keys(validationErrors).length) {
    console.log(form.value);
  }
};

const validateForm = (formData) => {
  const validationErrors = {};

  const validationRules = {
    login: {
      required: "Login is required",
    },
    password: {
      required: "Password is required",
    },
  };
  for (const field in validationRules) {
    if (!formData[field] && validationRules[field].required) {
      validationErrors[field] = validationRules[field].required;
    }
  }
  return validationErrors;
};

provide("formData", form);
provide("formErrors", errors);
</script>
