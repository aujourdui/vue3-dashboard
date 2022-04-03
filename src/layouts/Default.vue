<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { MenuIcon } from "@heroicons/vue/outline";
import { debounce } from "lodash";

const innerWidth = ref(window.innerWidth);
const show = ref(innerWidth.value >= 1280 ? true : false);

const checkWindowSize = () => {
  if (window.innerWidth >= 1280) {
    if (show.value === false && innerWidth.value < 1280) {
      show.value = true;
    } else {
      if (show.value === true) show.value = false;
    }
    innerWidth.value = window.innerWidth;
  }
};

onMounted(() => {
  window.addEventListener("resize", debounce(checkWindowSize, 100));
});

onUnmounted(() => {
  window.removeEventListener("resize", checkWindowSize);
});
</script>

<template>
  <div class="relative">
    <div
      class="fixed top-0 w-64 h-screen bg-white dark:bg-gray-800 z-20 transform duration-300 dark:text-gray-300"
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
      class="bg-gray-100 dark:bg-gray-900 h-screen overflow-hidden duration-300"
      :class="{ 'xl:pl-64': show }"
    >
      <div class="bg-white dark:bg-gray-800 rounded shadow m-4 p-4">
        <MenuIcon
          class="h-6 w-6 text-gray-600 dark:text-gray-300 cursor-pointer"
          @click="show = !show"
        />
      </div>
      <div class="dark:text-gray-300">
        <slot />
      </div>
    </div>
    >
  </div>
</template>

<style></style>
