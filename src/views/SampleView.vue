<script setup lang="ts">
import { defineProps } from "vue";

defineProps<{ displayText: string }>();
</script>

<template>
    <div class="sample">
        <h1>{{ displayText }}</h1>
    </div>
</template>

<style>
.sample {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

@media (min-width: 1024px) {
    .sample {
        min-height: 100vh;
        display: flex;
        align-items: center;
    }
}
</style>
