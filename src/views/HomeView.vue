<script setup>
import Hero from '@/components/Hero.vue';
import HomeCards from '@/components/HomeCards.vue';
import JobsListings from '@/components/JobsListings.vue';
import JobsListingsLive from '@/components/JobsListingsLive.vue';
</script>

<template>
  <Hero title="Find Your Dream Job" subtitle="Explore thousands of job opportunities that match your skills" />
  <HomeCards />
  <!-- <JobsListings :limit="2" :showButton="true" /> -->
  <JobsListingsLive :limit="2" :showButton="true" />
</template>
