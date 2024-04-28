<script setup lang="ts">
import { defineProps } from "vue";
const props = defineProps<{ color: string }>();
</script>

<template>
    <div>
        <div class="card-bg" :style="{ backgroundColor: props.color }" />
    </div>
</template>

<style>
.card-bg {
    width: 150px;
    height: 300px;
    margin: 10px;
}
</style>
