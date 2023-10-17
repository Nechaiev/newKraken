<template>
  <div>
    <button
      v-for="(component, label) in tabs"
      :key="label"
      :class="['tab-button', { active: currentTab === label }]"
      @click="currentTab = label"
    >
      {{ label }}
    </button>
    <component :is="tabs[currentTab]" class="tab"></component>
  </div>
</template>

<script setup>
import RolesFormStudent from "@/components/vee-validate-form/RolesFormStudent.vue";
import RolesFormTeacher from "@/components/vee-validate-form/RolesFormTeacher.vue";

import { ref } from "vue";

const currentTab = ref("Домівка");

const tabs = {
  Teacher: RolesFormTeacher,
  Student: RolesFormStudent,
};
</script>
