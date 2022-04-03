<script setup>
import { ref } from "vue";
import { MenuIcon } from "@heroicons/vue/outline";

const show = ref(true);
</script>

<template>
  <div class="relative">
    <div
      class="fixed top-0 w-64 h-screen bg-white z-20 transform duration-300"
      :class="{ '-translate-x-full': !show }"
    >
      Side bar
    </div>
    <div
      class="fixed xl:hidden inset-0 bg-gray-900 opacity-50 z-10"
      @click="show = !show"
      v-show="show"
    ></div>
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
