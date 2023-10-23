<template>
  <div class="container">
    <input type="text" v-model="myInput" class="border border-gray-600" />
    <text-field name="name" v-model="myInput" sync-v-model/>
    <!--        <login-form/>-->
    <!--        <age-login-form/>-->
    <!--    <vee-validate />-->
    <!--      <roles-form/>-->
    <!--    <dynamic-components />-->
    <!--    <roles-form-new />-->
    <roles-form-for-modal
      @success="onSuccess"
      @error="onError"
      v-model="myInput"
    />
    <!--  :myInput="myInput" @input="onInput"-->
    <!--  v-model:myInput="myInput"-->
  </div>
</template>

<script setup>
import LoginForm from "@/components/provide-inject/LoginForm.vue";
import AgeLoginForm from "@/components/provide-inject/AgeLoginForm.vue";
import {ref, watch} from "vue";
import VeeValidate from "@/components/provide-inject/VeeValidate.vue";
import RolesForm from "@/components/vee-validate-form/RolesForm.vue";
import DynamicComponents from "@/components/vee-validate-form/DynamicComponents.vue";
import RolesFormNew from "@/components/vee-validate-form/RolesFormNew.vue";
import RolesFormForModal from "@/components/vee-validate-form/RolesFormForModal.vue";
import TextField from "@/components/vee-validate-form/TextField.vue";

const myInput = ref("");

const onInput = (val) => {
  myInput.value = val;
};
const onSuccess = () => {
  alert("onSuccess");
};

const onError = () => {
  alert("onError");
};

</script>
<!--1. function random()-->
<!--2. event success -->
<!--3. Handler (перехоплювач) -->
<!--4. умова для виклику івентів  -->
