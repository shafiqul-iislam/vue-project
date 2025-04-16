<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <div class="container text-center py-5">
        <h1 class="display-1 fw-bold text-danger">404</h1>
        <p class="fs-3 text-muted">Oops! Page not found.</p>

        <RouterLink to="/" class="btn btn-success btn-sm">Go Back Home</RouterLink>
    </div>
</template>