
<template>
  <div class="container">
    <!--        <login-form/>-->
    <!--        <age-login-form/>-->
    <!--    <vee-validate />-->
      <roles-form/>
  </div>
</template>

<script setup>
import LoginForm from "@/components/provide-inject/LoginForm.vue";
import AgeLoginForm from "@/components/provide-inject/AgeLoginForm.vue";
import { ref } from "vue";
import VeeValidate from "@/components/provide-inject/VeeValidate.vue";
import RolesForm from "@/components/vee-validate-form/RolesForm.vue";

const input = ref("");
</script>
