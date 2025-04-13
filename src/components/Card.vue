<script setup>
import { defineProps } from 'vue';

defineProps({
    bg: {
        type: String,
        default: 'bg-white'
    }

});
</script>

<template>
    <div v-bind:class="`card shadow-sm ${bg}`">
        <slot></slot>
    </div>
</template>