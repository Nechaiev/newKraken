<template>
  <div class="flex justify-center items-center">
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded cursor-pointer m-6"
      @click="openModal = true"
    >
      OPEN A MODAL WINDOW
    </button>
    <Teleport to="body">
      <div
        v-if="openModal"
        class="fixed z-50 top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-white rounded p-4 shadow-lg"
      >
        <p class="text-xl mb-4">confirm sending data</p>
        <button
          @click="confirmForm"
          class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded cursor-pointer w-full"
        >
          CONFIRM
        </button>
        <button
          @click="openModal = false"
          class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded cursor-pointer w-full mt-4"
        >
          REJECT
        </button>
      </div>
    </Teleport>
  </div>
</template>

<script setup>
import { ref } from "vue";

const openModal = ref(false);

const values = ref(null)

// const onSubmit = (data) => {
//     console.log("Form submitted with data:", data);
// };
const confirmForm = () => {
    onSubmit(values.value);
    openModal.value = false;
};

</script>