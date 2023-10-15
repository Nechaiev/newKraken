<template>
  <form
    @submit="onSubmit"
    class="flex flex-col items-center border-2 px-6 py-10 max-w-xl mx-auto mb-6 rounded-[4px]"
  >
    <label>Select your role:</label>
    <validation-field
      type="radio"
      name="person"
      :label="key"
      v-for="(value, key) in PERSONS"
      :value="value"
      :key="value"
    />
    <validation-field
      type="email"
      name="email"
      label="Email"
      placeholder="Your email"
    />
    <validation-field
      name="phoneNumber"
      type="phone"
      placeholder="(999) 99-99-999"
      v-if="values.person === PERSONS.Teacher"
      v-mask="'+38 (000)-00-00-000'"
    />
    <validation-field
      type="text"
      name="series_passport"
      label="Series passport"
      placeholder="AA 123456"
      v-if="values.person === PERSONS.Teacher"
      v-mask="'SS 000000'"
    />
    <validation-field
      :type="showPassword ? 'text' : 'password'"
      name="password"
      label="password"
      placeholder="Your password"
    />
    <validation-field
      :type="showPassword ? 'text' : 'password'"
      name="confirmPassword"
      label="confirmPassword"
      placeholder="Confirm password"
    />
    <div class="flex items-center my-2">
      <input
        type="checkbox"
        class="form-checkbox h-5 w-5 text-green-500"
        id="togglePassword"
        v-model="showPassword"
      />
      <label for="togglePassword" class="ml-2">Show Password</label>
    </div>

    <button
      class="w-full py-2 px-4 bg-blue-500 hover:bg-blue-600 text-white font-sans rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500"
    >
      Submit
    </button>
    <pre>{{ errors }}</pre>
    <pre>{{ values }}</pre>
  </form>
</template>

<script setup>
import * as yup from "yup";
import "yup-phone";
import { useForm } from "vee-validate";
import ValidationField from "@/components/vee-validate-form/ValidationField.vue";
import { ref } from "vue";

const showPassword = ref(false);

const PERSONS = {
  Teacher: "Teacher",
  Student: "Student",
};

const initialValue = {
  person: PERSONS.Teacher,
  name: "",
};

const { handleSubmit, values, errors } = useForm({
  validationSchema: yup.object({
    email: yup.string().required().email(),

    phoneNumber: yup.string().when("person", {
      is: PERSONS.Teacher,
      then: (schema) => schema.required().min(13),
    }),

    series_passport: yup.string().when("person", {
      is: PERSONS.Teacher,
      then: (schema) => schema.required().min(8),
    }),

    password: yup.string().required().min(6),

    confirmPassword: yup
      .string()
      .required()
      .min(6)
      .oneOf([yup.ref("password")]),
  }),
});

const onSubmit = handleSubmit((values) => {
  console.log(JSON.stringify(values, null, 2));
});
</script>
