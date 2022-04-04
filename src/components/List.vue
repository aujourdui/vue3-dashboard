<script setup>
import { reactive } from "vue";

const lists = reactive([
  {
    name: "Dashboard",
    icon: "TemplateIcon",
    link: "/",
  },
  {
    name: "EC",
    icon: "ShoppingCartIcon",
    link: "/#",
    sublists: [
      {
        name: "Product list",
        link: "/#",
      },
      {
        name: "Order list",
        link: "/#",
      },
    ],
  },
]);
</script>

<template>
  <ul class="text-gray-700">
    <li class="mb-1" v-for="list in lists" :key="list.name">
      <a
        :href="list.link"
        class="block p-2 rounded-sm hover:text-white hover:bg-blue-400"
      >
        <span>{{ list.name }}</span>
      </a>
    </li>
  </ul>
</template>
