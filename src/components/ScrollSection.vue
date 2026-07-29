<template>
  <div ref="el" class="scroll-animate" :class="{ 'animate-in': isVisible }">
    <slot></slot>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const el = ref(null);
const isVisible = ref(false);
let observer = null;

const handleIntersect = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      isVisible.value = true;
    }
  });
};

onMounted(() => {
  if (el.value) {
    observer = new IntersectionObserver(handleIntersect, {
      threshold: 0.15,
      rootMargin: '0px 0px -50px 0px',
    });
    observer.observe(el.value);
  }
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});
</script>