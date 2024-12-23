<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCard.vue";
import JobListings from "@/components/jobListings.vue";
</script>
<template>
  <Hero
    title="Fraz Shabbir"
    subtitle="Find the Vue job that fits your skills and needs"
  />
  <HomeCards />
  <JobListings :limit="3" :showButton="true" />
</template>
