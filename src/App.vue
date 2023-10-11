<template>
    <div class="container ">
<!--        <login-form/>-->
        <age-login-form/>
    </div>
</template>

<script setup>
import LoginForm from "@/components/privide-inject/LoginForm.vue";
import AgeLoginForm from "@/components/privide-inject/AgeLoginForm.vue";
import {ref} from "vue";

const input = ref('')
</script>

