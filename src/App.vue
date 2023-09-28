<script setup>
import FieldTest from "@/components/UI/fieldTest/FieldTest.vue";
import MyInputTest from "@/components/UI/fieldTest/MyInputTest.vue";
import { ref, computed } from "vue";
import MyInput from "@/components/UI/fields/MyInput.vue";

const props = defineProps({
  message: String
})

const message = ref("");

</script>
<template>
  <div :class="containerClasses"
       class="container bg-slate-100 flex flex-col gap-8 m-10">
    <my-input
        class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm"
        v-model="message"
    />
    <p class="pl-2">{{ message }}</p>
    <input
        class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm"
        v-model="message"
        placeholder="Additional input"
    />
    <p class="pl-2">Value inputValue: {{ message }}</p>
    <!--  <div>-->
    <!--    <field-test  label="Name"-->
    <!--                 error="Name must be unique"-->
    <!--                 help="write your name"-->
    <!--                 required-->
    <!--    />-->
    <!--    <my-input-test placeholder="Brad Pitt"-->
    <!--                   type="text" />-->
    <!--  </div>-->
  </div>
</template>
