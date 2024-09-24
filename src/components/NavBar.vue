<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const isOpen = ref(false)
</script>

<template>
    <nav class="flex flex-col md:flex-row bg-gray-100 md:justify-between md:items-center">
        <div class="flex justify-between px-3 py-2">
            <div class="text-3xl font-serif">Logo</div>
            <button class="md:hidden" @click="isOpen = !isOpen">
                <i :class="{ 'ri-menu-line': !isOpen, 'ri-close-line': isOpen}" class="text-3xl text-blue-400"></i>
            </button>
        </div>
        <div v-show="isOpen" class="md:hidden flex flex-col space-y-3 bg-gray-200 px-3 py-4">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </div>
        <div class="hidden md:flex space-x-4 px-3">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </div>
    </nav>
</template>