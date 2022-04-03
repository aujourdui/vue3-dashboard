<script setup>
import { ref } from "vue";
import { MenuIcon } from "@heroicons/vue/outline";

const show = ref(true);
</script>

<template>
  <div class="relative">
    <div
      class="fixed top-0 w-64 h-screen bg-white z-20 transform"
      :class="{ '-translate-x-full': !show }"
    >
      Side bar
    </div>
    <div
      class="bg-gray-100 h-screen overflow-hidden"
      :class="{ 'xl:pl-64': show }"
    >
      <div class="bg-white rounded shadow m-4 p-4">
        <MenuIcon
          class="h-6 w-6 text-gray-600 cursor-pointer"
          @click="show = !show"
        />
      </div>
      <div>
        <slot />
      </div>
    </div>
    >
  </div>
</template>

<style></style>
