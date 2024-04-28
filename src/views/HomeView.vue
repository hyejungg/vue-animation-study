<script setup lang="ts">
import { onMounted } from "vue";
import TheWelcome from "../components/TheWelcome.vue";
import AboutView from "./AboutView.vue";
import CardView from "./CardView.vue";
import SampleView from "./SampleView.vue";

// IntersectionObserver 를 등록한다.
const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
        // 관찰 대상이 viewport 안에 들어온 경우 'animate' 클래스를 추가
        if (entry.intersectionRatio > 0) {
            entry.target.classList.add("animate");

            // 애니메이션 적용 후 해당 요소의 관찰 중지
            // observer.unobserve(entry.target);
        }
        // 그 외의 경우 'animate' 클래스 제거
        else {
            entry.target.classList.remove("animate");
        }
    });
});

onMounted(() => {
    // 해당 페이지에 존재하는 모든 item 요소를 관찰
    const items = document.querySelectorAll(".item");
    items.forEach((el) => {
        observer.observe(el);
    });
});
</script>

<template>
    <main>
        <TheWelcome />
        <div class="scrollArea">
            <AboutView class="item" />
            <SampleView class="item" display-text="history" />
            <CardView class="item" />
        </div>
    </main>
</template>

<style>
@import url("../assets/common-animate.css");
</style>
