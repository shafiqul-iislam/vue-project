<script setup>
import logo from '../assets/logo.svg';
</script>

<template>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-success border-bottom">
        <div class="container">
            <div class="">
                <a class="navbar-brand" href="#">JobFinder</a>
                <img :src="logo" alt="" style="width: 20px; height: 15px;">
            </div>

            <div class="collapse navbar-collapse">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link active" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Jobs</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>