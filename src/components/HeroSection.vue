<template>
  <section class="relative h-screen flex items-center justify-center overflow-hidden" id="hero">
    <canvas ref="canvas"
      class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-screen h-screen object-cover"></canvas>
    <div class="absolute inset-0 bg-black/60"></div>
    <div class="relative z-10 text-center text-white px-4 max-w-4xl mx-auto" data-aos="zoom-in-up">
      <div class="absolute top-0 inset-x-0 h-64 flex items-start">
        <div class="h-24 w-2/3 bg-gradient-to-br from-[#570cac] blur-2xl invisible opacity-40"></div>
        <div class="h-20 w-3/5 bg-gradient-to-r from-[#670ccf] blur-2xl opacity-40"></div>
      </div>
      <div class="w-full px-5 sm:px-12 lg:px-8 max-w-screen-lg lg:max-w-screen-xl mx-auto relative">
        <div class="flex justify-between flex-col items-center md:flex-row lg:flex-row gap-10 xl:gap-14 relative pt-24 lg:max-w-none md:max-w-3xl mx-auto">
          <!-- Left section for h1 and buttons -->
          <div class="lg:py-6 flex-1 text-left">
            <div class="lg:text-left">
               <h1
              class="pt-4 text-white font-bold text-4xl md:text-5xl lg:text-6xl"
            >
              Hi, I'm
              <span
                class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-pink-500"
              >
                Hassan
              </span>
            </h1>
            </div>
            <div class="flex items-center justify-center gap-3 pt-9 flex-col sm:flex-row sm:w-max sm:mx-auto lg:mx-0">
              <button
                class="border border-primary px-6 md:px-7 py-3 rounded-full relative group w-full sm:w-max flex justify-center">
                <span
                  class="absolute inset-0 rounded-3xl group-hover:scale-105 origin-center transition-all ease-in-out bg-primary border-2 border-transparent"></span>
                <span class="relative flex items-center justify-center text-white">
                  <a href="#contact">Hire Me</a>
                </span>
              </button>
              <button
                class="border border-primary px-6 md:px-7 py-3 rounded-full relative group w-full sm:w-max flex justify-center">
                <div class="hover:scale-105 transition-all ease-in-out flex justify-center items-center relative">
                  <div class="svg-container">
                    <div class="download-loader text-white hidden"></div>
                  </div>
                  <a href="../assets/Cv Frontend Hassan 22-07-2025.pdf" download="Cv Frontend Hassan 22-07-2025.pdf"
                    class="pl-2 text-white">Download resume</a>
                </div>
              </button>
            </div>
          </div>

          <!-- Right section for the paragraph -->
          <div class="lg:h-full md:flex flex-1 items-center justify-end  text-left">
            <p class="text-gray-300 pt-8 mx-auto max-w-xl">
              <span class="text-transparent font-bold bg-clip-text bg-gradient-to-r from-white to-pink-500">Software
                Engineer (Frontend) </span>( seek to contribute to innovative projects and develop outstanding
              user experiences using the latest technologies and tools. I am a
              fast learner, and my goal is to continue learning new technologies )
            </p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const canvas = ref(null);
const imageCount = 199;
const images = [];
const imagePaths = Array.from({ length: imageCount }, (_, i) => {
  const frame = String(i + 1).padStart(3, "0");
  return `${import.meta.env.BASE_URL}imgs/ezgif-frame-${frame}.jpg`;
});

const preloadImages = () => {
  for (let i = 0; i < imageCount; i++) {
    const img = new Image();
    img.src = imagePaths[i];
    images.push(img);
  }
};

const handleScroll = () => {
  const scrollTop = document.documentElement.scrollTop;
  const maxScrollTop = document.documentElement.scrollHeight - window.innerHeight;
  const scrollFraction = scrollTop / maxScrollTop;
  const frameIndex = Math.min(
    imageCount - 1,
    Math.ceil(scrollFraction * imageCount)
  );

  const context = canvas.value.getContext('2d');
  const img = images[frameIndex];
  if (img && img.complete) {
    canvas.value.width = img.width;
    canvas.value.height = img.height;
    context.drawImage(img, 0, 0);
  }
};

onMounted(() => {
  preloadImages();
  const context = canvas.value.getContext('2d');
  const initialImage = new Image();
  initialImage.src = imagePaths[0];
  initialImage.onload = () => {
    canvas.value.width = initialImage.width;
    canvas.value.height = initialImage.height;
    context.drawImage(initialImage, 0, 0);
    window.addEventListener('scroll', handleScroll);
  };
});
</script>