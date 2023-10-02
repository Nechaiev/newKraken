<script setup>
import { ref } from "vue";
import CustomInput from "@/components/CustomInput.vue";

const form = ref({
  login: "",
  password: "",
});
const onSubmit = () => {
  console.log(form.value);
};
</script>

<template>
  <form @submit.prevent="onSubmit">
    <custom-input
        name="login"
        v-model="form.login"
    />
    <custom-input
      type="password"
      name="password"
      v-model="form.password"
    />
    <custom-input
      type="password"
      name="password"
      :modelValue="form.password"
      @update:modelValue="form.password = $event"
    />
    <button class="text-black border-black rounded p-2 border-solid border-2">Submit</button>
  </form>
</template>