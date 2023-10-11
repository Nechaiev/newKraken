<template>
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
    <div class="mb-4">
      <custom-input type="date" name="birthdate" class="mb-2" />
    </div>
    <button
      class="w-full py-2 px-4 bg-blue-500 hover:bg-blue-600 text-white font-sans rounded-full focus:outline-none focus:ring-2 focus:ring-blue-500"
    >
      Submit
    </button>
  </form>
</template>

<script setup>
import CustomInput from "@/components/privide-inject/CustomInput.vue";
import { useForm } from "@/composables/form.js";
import { object, string, date } from "yup";

const { form, errors, checkIsValid } = useForm(
  {
    login: "",
    password: "",
    birthdate: "",
  },
  object({
    login: string().min(5).max(20).email(),
    password: string().min(5),
    birthdate: date()
      .required()
      .test("age", "You must be 18 or older", (value) => {
        const today = new Date();
        const userBirthdate = new Date(value);
        let age = today.getFullYear() - userBirthdate.getFullYear();
        if (
          today.getMonth() < userBirthdate.getMonth() ||
          (today.getMonth() === userBirthdate.getMonth() &&
            today.getDate() < userBirthdate.getDate())
        ) {
          age--;
        }
        return age >= 18;
      }),
  }),
);

const onSubmit = async () => {
  if (await checkIsValid()) {
    console.log(form.value);
  }
};
const clearError = (fieldName) => {
  errors.value[fieldName] = "";
};
</script>
