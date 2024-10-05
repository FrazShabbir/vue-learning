<script setup>
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import Cards from "@/components/HomeCard.vue";
import JobListings from "@/components/jobListings.vue";
</script>
<template>
  <Navbar />
  <Hero
    title="Fraz Shabbir"
    subtitle="Find the Vue job that fits your skills and needs"
  />
  <Cards />
  <JobListings :limit="3" :showButton="true" />
</template>

<style scoped></style>
