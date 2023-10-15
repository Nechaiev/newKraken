<template>
  <pre>
    {{ form }}
  </pre>
  <pre>
    {{ errors }}
  </pre>
  <form
    @submit.prevent="onSubmit"
    class="max-w-md mx-auto my-4 p-4 bg-white rounded-lg shadow-lg"
  >
    <div class="mb-4">
      <custom-input name="login" class="mb-2" />
    </div>
    <div class="mb-4">
      <custom-input type="password" name="password" class="mb-2" />
    </div>
    <button
      class="w-full py-2 px-4 bg-blue-500 hover:bg-blue-600 text-white font-semibold rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500"
    >
      Submit
    </button>
  </form>
</template>

<script setup>
import { watch } from "vue";
import CustomInput from "@/components/provide-inject/CustomInput.vue";
import { useForm } from "@/composables/form.js";
import { object, string } from "yup";

const { form, errors, checkIsValid } = useForm(
  {
    login: "",
    password: "",
  },
  object({
    login: string().min(5).max(20).email(),
    password: string().min(5),
  }),
);

const onSubmit = async () => {
  if (await checkIsValid()) {
    console.log(form.value);
  }
  // const validationErrors = validator();
  //
  // Object.keys(validationErrors).forEach((field) => {
  //   errors.value[field] = validationErrors[field];
  // });
  //
  // if (Object.keys(validationErrors).length === 0) {
  //   console.log(form.value);
  // }
};

const clearError = (fieldName) => {
  errors.value[fieldName] = "";
};

// const validator = () => {
//   const validationErrors = {};
//
//   if (!form.value.login) {
//     validationErrors.login = "Login is required";
//   }
//
//   if (!form.value.password) {
//     validationErrors.password = "Password is required";
//   }
//
//   return validationErrors;
// };

// watch(form, () => {
//   const validationErrors = validator();
//   Object.keys(errors.value).forEach((field) => {
//     errors.value[field] = validationErrors[field] || "";
//   });
// });
</script>

//old version
<!--<template>-->
<!--  <form-->
<!--    @submit.prevent="onSubmit"-->
<!--    class="max-w-lg mx-auto my-4 p-4 bg-white rounded-lg shadow-lg"-->
<!--  >-->
<!--    <pre>{{ form }}</pre>-->
<!--    <custom-input-->
<!--      name="login"-->
<!--      v-model="form.login"-->
<!--      :error="errors.login"-->
<!--      label="Login"-->
<!--      class="mb-2"-->
<!--    />-->
<!--    <custom-input-->
<!--      v-model="form.password"-->
<!--      :error="errors.password"-->
<!--      label="Password"-->
<!--      type="password"-->
<!--      name="password"-->
<!--      class="mb-2"-->
<!--    />-->
<!--    <button class="text-black border-black rounded p-2 border-solid border-2">-->
<!--      Submit-->
<!--    </button>-->
<!--  </form>-->
<!--</template>-->

<!--<script setup>-->
<!--import { provide, ref } from "vue";-->
<!--import CustomInput from "@/components/provide-inject/CustomInput.vue";-->

<!--const form = ref({-->
<!--  login: "",-->
<!--  password: "",-->
<!--});-->
<!--const errors = ref({-->
<!--  login: "",-->
<!--  password: "",-->
<!--});-->
<!--const onSubmit = () => {-->
<!--  console.log(form.value);-->
<!--  const validationErrors = validateForm(form.value);-->
<!--  Object.assign(errors.value, validationErrors);-->

<!--  if (!Object.keys(validationErrors).length) {-->
<!--    console.log(form.value);-->
<!--  }-->
<!--};-->

<!--const validateForm = (formData) => {-->
<!--  const validationErrors = {};-->

<!--  const validationRules = {-->
<!--    login: {-->
<!--      required: "Login is required",-->
<!--    },-->
<!--    password: {-->
<!--      required: "Password is required",-->
<!--    },-->
<!--  };-->
<!--  for (const field in validationRules) {-->
<!--    if (!formData[field] && validationRules[field].required) {-->
<!--      validationErrors[field] = validationRules[field].required;-->
<!--    }-->
<!--  }-->
<!--  return validationErrors;-->
<!--};-->

<!--provide("formData", form);-->
<!--provide("formErrors", errors);-->
<!--</script>-->
