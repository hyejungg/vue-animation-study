<script setup lang="ts">
import CardItem from "@/components/CardItem.vue";

const colors = ["blue", "red"];
</script>

<template>
    <div class="card">
        <CardItem v-for="color in colors" :key="color" :color="color" />
    </div>
</template>

<style>
.card {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

@media (min-width: 1024px) {
    .card {
        min-height: 100vh;
        display: flex;
        align-items: center;
    }
}
</style>
