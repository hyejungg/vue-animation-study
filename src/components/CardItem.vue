<script setup lang="ts">
import { defineProps, ref } from "vue";

const props = defineProps<{ color: string }>();
const containerRef = ref<HTMLDivElement | null>(null);
const isHovered = ref(false);
const handleMouseMove = (e: MouseEvent) => {
    if (containerRef.value) {
        const rect = containerRef.value.getBoundingClientRect();
        const x = e.clientX - rect.left - rect.width / 2;
        const y = e.clientY - rect.top - rect.height / 2;
        const rotateY = (x / rect.width) * 20;
        const rotateX = -(y / rect.height) * 20;
        containerRef.value.style.transform = `perspective(500px) rotateY(${rotateY}deg) rotateX(${rotateX}deg)`;
    }
};

const handleMouseEnter = () => {
    isHovered.value = true;
};

const handleMouseLeave = () => {
    isHovered.value = false;
    if (containerRef.value) {
        containerRef.value.style.transform = "none";
    }
};

const handleClick = () => {
    window.open("https://www.naver.com", "_blank");
};
</script>

<template>
    <div
        class="container"
        ref="containerRef"
        @mousemove="handleMouseMove"
        @mouseenter="handleMouseEnter"
        @mouseleave="handleMouseLeave"
    >
        <div
            class="card-bg front"
            :style="{ backgroundColor: props.color }"
            v-if="!isHovered"
        ></div>
        <div
            class="card-bg back"
            :style="{
                border: `2px solid ${props.color}`,
            }"
            v-else
            @click="handleClick"
        >
            <div>text ~~</div>
            <div>text2222</div>
        </div>
    </div>
</template>

<style>
.card-bg {
    width: 150px;
    height: 300px;
    margin: 10px;
}
.back {
    background-color: white;
    color: black;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
</style>
