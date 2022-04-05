<script setup>
import { reactive } from "vue";

import {
  TemplateIcon,
  ShoppingCartIcon,
  ChevronDownIcon,
} from "@heroicons/vue/outline";

const icons = {
  TemplateIcon: TemplateIcon,
  ShoppingCartIcon: ShoppingCartIcon,
};

const toggle = (name) => {
  const list = lists.find((list) => list.name === name);
  list.show = !list.show;
};

const enter = (element) => {
  element.style.height = "auto";
  const height = getComputedStyle(element).height;
  element.style.height = 0;
  getComputedStyle(element);
  setTimeout(() => {
    element.style.height = height;
  });
};

const leave = (element) => {
  element.style.height = getComputedStyle(element).height;
  getComputedStyle(element);
  setTimeout(() => {
    element.style.height = 0;
  });
};

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
    show: false,
    sublists: [
      {
        name: "Product list",
        link: "/product",
      },
      {
        name: "Order list",
        link: "/order",
      },
    ],
  },
]);
</script>

<template>
  <ul class="text-gray-700 dark:text-gray-300">
    <li class="mb-1" v-for="list in lists" :key="list.name">
      <RouterLink
        v-if="!list.sublists"
        :to="list.link"
        class="flex items-center block p-2 rounded-sm hover:text-white hover:bg-blue-400"
      >
        <component :is="icons[list.icon]" class="w-6 h-6 mr-2"></component>
        <span>{{ list.name }}</span>
      </RouterLink>
      <div
        v-else
        class="flex items-center justify-between p-2 cursor-pointer rounded-sm hover:bg-blue-400 hover:text-white"
        @click="toggle(list.name)"
      >
        <div class="flex items-center">
          <component :is="icons[list.icon]" class="w-6 h-6 mr-2"></component>
          <span>
            {{ list.name }}
          </span>
        </div>
        <ChevronDownIcon
          class="w-4 h-4 transform duration-300"
          :class="!list.show ? '-rotate-90' : 'rotate-0'"
        />
      </div>
      <Transition @enter="enter" @leave="leave">
        <ul class="mt-1 overflow-hidden" v-show="list.show">
          <li class="mb-1" v-for="list in list.sublists" :key="list.name">
            <RouterLink
              :to="list.link"
              class="block p-2 rounded-sm hover:bg-blue-400 hover:text-white"
            >
              <span class="pl-8">{{ list.name }}</span>
            </RouterLink>
          </li>
        </ul>
      </Transition>
    </li>
  </ul>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: height 0.3s;
}
</style>
