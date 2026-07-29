<template>
  <div class="fixed top-0 left-0 w-full h-1 z-50">
    <div class="h-full bg-gradient-to-r from-blue-500 to-purple-600 transition-all duration-100" :style="{ width: progress + '%' }"></div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const progress = ref(0);
let ticking = false;

const updateProgress = () => {
  const scrollTop = document.documentElement.scrollTop;
  const maxScroll = document.documentElement.scrollHeight - window.innerHeight;
  progress.value = maxScroll > 0 ? (scrollTop / maxScroll) * 100 : 0;
  ticking = false;
};

const onScroll = () => {
  if (!ticking) {
    requestAnimationFrame(updateProgress);
    ticking = true;
  }
};

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true });
});

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll);
});
</script>