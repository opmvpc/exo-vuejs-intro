<script setup>
const props = defineProps({
    type: {
        type: String,
        default: "primary"
    },
    isDisabled: {
        type: Boolean,
    }
})
</script>

<template>
    <button class="rounded shadow px-4 py-1" :class="{
        'bg-blue-200 text-blue-800': props.type === 'primary',
        'bg-gray-200 text-gray-800': props.type === 'secondary', 'bg-red-200 text-red-800': props.type === 'danger',
        'cursor-not-allowed opacity-60': props.isDisabled
    }" :disabled="props.isDisabled">
        <slot></slot>
    </button>
</template>