<script setup>
import Hero from '@/components/Hero.vue';
import HomeCards from '@/components/HomeCards.vue';
import JobListing from '@/components/JobListing.vue';
</script>

<template>
    <Hero title="Test Title" subtitle="Testy subtitle"></Hero>
    <HomeCards></HomeCards>
    <JobListing :limit="4" :showButton=true></JobListing>
</template>