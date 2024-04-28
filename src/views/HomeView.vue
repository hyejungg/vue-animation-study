<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import AboutView from './AboutView.vue'
import CardView from './CardView.vue'
import SampleView from './SampleView.vue'
</script>

<template>
  <main>
    <TheWelcome />
    <AboutView />
    <SampleView display-text="history" />
    <CardView />
  </main>
</template>
