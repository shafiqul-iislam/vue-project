<script setup>
import { defineProps } from 'vue';

defineProps({
    title: {
        type: String,
        default: 'Find Your Dream Job'
    },
    subtitle: {
        type: String,
        default: 'Explore thousands of job opportunities that match your skills'
    }
})
</script>

<template>
    <!-- Hero Header -->
    <header class="hero-header text-center text-white bg-success py-5">
        <h1 class="display-4 fw-bold">{{ title }}</h1>
        <p class="lead mt-2">{{ subtitle }}</p>
    </header>
</template>