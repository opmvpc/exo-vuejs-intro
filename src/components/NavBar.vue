<script setup>
import { ref } from "vue";
import { RouterLink } from "vue-router";

const links = [
  {
    label: "Home",
    lien: "/",
  },
  {
    label: "About",
    lien: "/about",
  },
  {
    label: "Pays",
    lien: "/flags",
  },
  {
    label: "Contact",
    lien: "/contact",
  },
];

const isOpen = ref(false);
</script>

<template>
  <nav
    class="flex flex-col md:flex-row bg-gray-100 md:justify-between md:items-center"
  >
    <div class="flex justify-between px-3 py-2">
      <div class="text-3xl font-serif">
        <RouterLink to="/">Logo</RouterLink>
      </div>
      <button class="md:hidden" @click="isOpen = !isOpen">
        <i
          :class="{ 'ri-menu-line': !isOpen, 'ri-close-line': isOpen }"
          class="text-3xl text-blue-400"
        ></i>
      </button>
    </div>
    <div
      v-show="isOpen"
      class="md:hidden flex flex-col space-y-3 bg-gray-200 px-3 py-4"
    >
      <RouterLink
        v-for="(link, index) in links"
        :to="link.lien"
        :key="`lien-responsive-${index}`"
        >{{ link.label }}</RouterLink
      >
    </div>
    <div class="hidden md:flex space-x-4 px-3">
      <RouterLink
        v-for="(link, index) in links"
        :to="link.lien"
        :key="`lien-${index}`"
        >{{ link.label }}</RouterLink
      >
    </div>
  </nav>
</template>
