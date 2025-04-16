<script setup>
import logo from '../assets/logo.svg';
import { RouterLink, useRouter } from 'vue-router';

const isActiveLink = (routePath) => {
    const router = useRouter();
    return router.currentRoute.value.path === routePath;
}
</script>

<template>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-success border-bottom">
        <div class="container">
            <div class="">
                <RouterLink class="navbar-brand" to="/">JobFinder</RouterLink>
                <img :src="logo" alt="" style="width: 20px; height: 15px;">
            </div>

            <div class="collapse navbar-collapse">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <RouterLink :class="[isActiveLink('/') ? 'bg-dark' : '', 'nav-link', 'rounded', 'text-white']"
                            to="/">Home
                        </RouterLink>
                    </li>
                    <li class="nav-item">
                        <RouterLink
                            :class="[isActiveLink('/jobs') ? 'bg-dark' : '', 'nav-link', 'rounded', 'text-white']"
                            to="/jobs">
                            Jobs
                        </RouterLink>
                    </li>
                    <li class="nav-item">
                        <RouterLink
                            :class="[isActiveLink('/add-job') ? 'bg-dark' : '', 'nav-link', 'rounded', 'text-white']"
                            to="/add-job">
                            Add Job
                        </RouterLink>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>