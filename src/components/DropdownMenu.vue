<script setup>
import { UserIcon, LogoutIcon } from "@heroicons/vue/outline";
</script>

<template>
  <div class="relative">
    <img
      src="../assets/avatar.jpeg"
      class="rounded-full w-10 h-10 cursor-pointer"
    />
    <div
      class="absolute top-16 right-0 z-10 w-40 py-2 bg-white rounded-sm shadow"
    >
      <ul>
        <li class="text-gray-700 hover:bg-blue-100 hover:text-blue-600 p-2">
          <a href="/#" class="flex items-center space-x-2">
            <UserIcon class="w-5 h-5" />
            <span class="text-sm font-bold">Profile</span>
          </a>
        </li>
        <li class="text-gray-700 hover:bg-blue-100 hover:text-blue-600 p-2">
          <a href="/#" class="flex items-center space-x-2">
            <LogoutIcon class="w-5 h-5" />
            <span class="text-sm font-bold">Logout</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>
