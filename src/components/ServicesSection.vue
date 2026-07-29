<template>
  <section class="text-white mt-20 sm:items-center" id="services">
    <div class="px-4 xl:pl-16">
      <h2 class="text-4xl font-bold text-white mb-4 text-center">
        My Services
      </h2>
    </div>
    <div
      class="py-8 xl:px-16 px-4 sm:py-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
    >
      <div
        v-for="service in services"
        :key="service.id"
        data-aos="fade-up"
        class="px-8 py-12 rounded-xl bg-gradient-to-r from-[#111a3e] to-[#350958]   shadow-lg border border-[#1f1641]"
      >
        <div class="mx-auto h-24 text-center xl:h-28 xl:w-28">
          <div class="flex justify-center">
            <img :src="service.icon" alt="service icon" />
          </div>
        </div>
        <div class="text-center">
          <h3
            class="pt-8 text-lg font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl"
          >
            {{ service.name }}
          </h3>
          <p class="text-grey pt-4 text-sm group-hover:text-white md:text-base">
            {{ service.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref } from "vue";
const services = ref([
  {
    id: 1,
    icon: "https://img.icons8.com/ios-filled/100/ffffff/google-code.png",
    name: "Web Development",
    description:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed, consequuntur.",
  },
  {
    id: 2,
    icon: "https://img.icons8.com/?size=100&id=102595&format=png&color=ffffff",
    name: "Graphic Design",
    description:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed, consequuntur.",
  },
  {
    id: 3,
    icon: "https://img.icons8.com/?size=100&id=u2ncVA91xE5q&format=png&color=ffffff",
    name: "Web Design",
    description:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed, consequuntur.",
  },

  {
    id: 4,
    icon: "https://img.icons8.com/?size=100&id=100050&format=png&color=ffffff",
    name: "Document controll manager",
    description:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed, consequuntur.",
  },
  {
    id: 5,
    icon: "https://img.icons8.com/?size=100&id=111248&format=png&color=ffffff",
    name: "Assistant",
    description:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed, consequuntur.",
  },
  {
    id: 6,
    icon: "https://img.icons8.com/?size=100&id=101315&format=png&color=ffffff",
    name: "Office manager",
    description:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed, consequuntur.",
  },
]);
import Aos from "aos";
import "aos/dist/aos.css";
Aos.init();
</script>
