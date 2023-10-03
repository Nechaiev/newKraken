<template>
    <form @submit.prevent="onSubmit" class="max-w-lg mx-auto my-4 p-4 bg-white rounded-lg shadow-lg">
        <pre>{{ form }}</pre>
        <custom-input name="login" class="mb-2"/>
        <custom-input type="password" name="password" class="mb-2"/>

        <!--    <custom-input-->
        <!--      type="password"-->
        <!--      name="password"-->
        <!--      :modelValue="form.password"-->
        <!--      @update:modelValue="form.password = $event"-->
        <!--    />-->
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
const onSubmit = () => {
  console.log(form.value);
};
provide("formData", form);
</script>