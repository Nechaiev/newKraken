<template>
  <Form
    @submit="onSubmit"
    v-slot="{ isSubmitting }"
    :initialValues="initialValue"
    :validationSchema="validationSchema"
    class="flex flex-col items-center border-2 px-6 py-10 max-w-xl mx-auto mb-6 rounded-[4px]"
  >
    <h3 class="block w-full text-3xl mb-8">Log in</h3>
    <vee-valid-field name="login" label="login" />
    <vee-valid-field type="email" name="email" label="email" />
    <vee-valid-field type="password" name="password" label="password" />
    <vee-valid-field type="date" name="date" label="date" />
    <button
      class="w-full py-2 px-4 bg-blue-500 hover:bg-blue-600 text-white font-sans rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500"
    >
      Submit
    </button>
  </Form>
</template>

<script setup>
import { Form } from "vee-validate";
import * as yup from "yup";
import VeeValidField from "@/components/provide-inject/VeeValidField.vue";

const initialValue = {
  date: "1976-07-20",
  login: "",
  email: "",
  password: "",
};

const validationSchema = {
  date: yup.string().min(5),
  login: yup.string().min(5),
  email: yup.string().required(),
  password: yup.string().required().min(8),
};

const onSubmit = async (...arr) => {
  await new Promise((resolve) => {
    setTimeout(() => {
      resolve(true);
    }, 4000);
  });
  console.log(arr);
};
</script>
