<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { UserIcon, LogoutIcon } from "@heroicons/vue/outline";

const show = ref(false);
const root = ref(null);

const toggle = () => {
  show.value = !show.value;
};

const clickOutSide = (e) => {
  if (!root.value.contains(e.target) && show.value) {
    show.value = false;
  }
};

onMounted(() => document.addEventListener("click", clickOutSide));
onUnmounted(() => document.removeEventListener("click", clickOutSide));
</script>

<template>
  <div class="relative" ref="root">
    <img
      src="../assets/avatar.jpeg"
      class="rounded-full w-10 h-10 cursor-pointer"
      @click="toggle"
    />
    <Transition
      enter-active-class="transition-opacity duration-300"
      enter-from-class="opacity-0"
      leave-active-class="transition-opacity duration-300"
      leave-to-class="opacity-0"
    >
      <div
        class="absolute top-16 right-0 z-10 w-40 py-2 bg-white rounded-sm shadow dark:bg-gray-800"
        v-show="show"
      >
        <ul>
          <li
            class="text-gray-700 dark:text-gray-300 hover:bg-blue-100 dark:hover:bg-gray-700 hover:text-blue-600 dark:hover:text-blue-600 p-2"
          >
            <a href="/#" class="flex items-center space-x-2">
              <UserIcon class="w-5 h-5" />
              <span class="text-sm font-bold">Profile</span>
            </a>
          </li>
          <li
            class="text-gray-700 dark:text-gray-300 hover:bg-blue-100 dark:hover:bg-gray-700 hover:text-blue-600 dark:hover:text-blue-600 p-2"
          >
            <a href="/#" class="flex items-center space-x-2">
              <LogoutIcon class="w-5 h-5" />
              <span class="text-sm font-bold">Logout</span>
            </a>
          </li>
        </ul>
      </div>
    </Transition>
  </div>
</template>
