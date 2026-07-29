<template>
  <header
    class="flex justify-between rounded-4xl md:w-[50%] w-[80%] top-3 items-center p-4 bg-gradient-to-r from-[#111a3e] to-[#350958] bg-opacity-90 fixed top-0 left-0 right-0 z-50 shadow-lg mx-auto"
  >
    <a href="#hero"
      class="text-3xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-primary to-pink-500" 
    >
      H
    </a>
    <!-- mobile Toggle Btn -->
    <div class="md:hidden z-30">
      <button
        type="button"
        class="block focus:outline-none"
        @click="isMenuOpen = !isMenuOpen"
      >
        <span v-if="isMenuOpen" class="text-5xl">
          <img
            src="https://img.icons8.com/ios-filled/100/ffffff/delete-sign.png"
            alt="close"
            width="30"
            height="30"
          />
        </span>

        <span v-else class="text-5xl">
          <img
            src="https://img.icons8.com/ios-filled/100/ffffff/menu--v6.png"
            alt="menu"
            width="30"
            height="30"
          />
        </span>
      </button>
    </div>
    <!-- navBar Links -->
    <nav
      :class="[
        'fixed inset-0 z-[60] flex flex-col items-center justify-center bg-[#111827]/95 backdrop-blur-lg md:relative md:bg-transparent md:flex md:justify-between md:flex-row ',
        isMenuOpen ? 'block' : 'hidden',
      ]"
    >
      <ul
        class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0"
      >
        <li v-for="item in Menu" :key="item.name">
          <a
            :href="item.href"
            class="block text-white transition hover:text-primary ease-linear text-2xl md:text-lg"
            @click="scrollToSection(item.href)"
            >{{ item.name }}</a
          >
        </li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref } from "vue";
const Menu = ref([
  { name: "Services", href: "#services" },
  { name: "About Me", href: "#about" },
  { name: "Skills", href: "#skills" },
  { name: "Projects", href: "#projects" },
  { name: "Testimonials", href: "#testimonials" },
  { name: "Contact", href: "#contact" },
]);

const isMenuOpen = ref(false);
const scrollToSection = (href) => {
  isMenuOpen.value = false;
  const section = document.querySelector(href);
  if (section) {
    section.scorollIntoView({ behavior: "smooth" });
  }
};
</script>
