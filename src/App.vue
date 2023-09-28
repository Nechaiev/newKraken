<script setup>
import MyButton from "@/components/MyButton.vue";
import {EnvelopeIcon} from '@heroicons/vue/24/solid';

</script>

<template>

  <div class="container bg-slate-100 flex flex-col gap-8 mx-auto p-8">
    <div class="flex gap-5">
      <my-button intent="primary" :left-icon="EnvelopeIcon">Primary</my-button>
      <my-button intent="secondary" :left-icon="EnvelopeIcon">Secondary</my-button>
      <my-button intent="danger" :left-icon="EnvelopeIcon">Danger</my-button>
      <my-button intent="text" :left-icon="EnvelopeIcon">Text</my-button>
    </div>
    <div class="flex gap-5">
      <my-button disabled intent="primary" :left-icon="EnvelopeIcon">Primary</my-button>
      <my-button disabled intent="secondary" :left-icon="EnvelopeIcon">Secondary</my-button>
      <my-button disabled intent="danger" :left-icon="EnvelopeIcon">Danger</my-button>
      <my-button disabled intent="text" :left-icon="EnvelopeIcon">Text</my-button>
    </div>
    <div class="flex gap-5">
      <my-button intent="primary" :right-icon="EnvelopeIcon">Primary</my-button>
      <my-button intent="secondary" :right-icon="EnvelopeIcon">Secondary</my-button>
      <my-button intent="danger" :right-icon="EnvelopeIcon">Danger</my-button>
      <my-button intent="text" :right-icon="EnvelopeIcon">Text</my-button>
    </div>
    <div class="flex gap-5">
      <my-button intent="primary" loading>Primary</my-button>
      <my-button intent="secondary" loading>Secondary</my-button>
      <my-button intent="danger" loading>Danger</my-button>
      <my-button intent="text" loading>Text</my-button>
    </div>
    <div class="flex gap-5">
      <my-button intent="primary">Primary</my-button>
      <my-button intent="secondary">Secondary</my-button>
      <my-button intent="danger">Danger</my-button>
      <my-button intent="text">Text</my-button>
    </div>
  </div>
</template>

<style scoped>

</style>
