<script setup>
import Navbar from '@/components/Navbar.vue';
import { RouterView } from 'vue-router';


// import Hero from '@/components/Hero.vue';
// import HomeCards from '@/components/HomeCards.vue';
// import JobsListings from './components/JobsListings.vue';
</script>

<template>
    <Navbar />
    <RouterView />


    <!-- <Hero title="Find Your Dream Job" subtitle="Explore thousands of job opportunities that match your skills" />
    <HomeCards />
    <JobsListings :limit="3" :showButton="true" /> -->
</template>