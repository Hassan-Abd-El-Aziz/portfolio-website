<template>
  <section class="text-white mt-20" id="projects">
    <div class="px-4 xl:pl-16">
      <div class="mb-4 md:flex md:justify-between xl:pr-16">
        <h2 class="text-4xl font-bold text-white">my Latest Projects</h2>
        <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
          <button
            class="hover:text-primary"
            v-for="category in ['all', 'web development', 'mobile App']"
            :key="category"
            @click="() => (SelectedCategory = category)"
          >
            {{ category }}
          </button>
        </div>
      </div>
      <ul
        class="px-4 sm:py-16 xl:pr-16 grid grid-cols-1 gap-10 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
        data-aos="fade-right"
      >
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="hover:scale-105 transition-all ease-in-out cursor-pointer"
        >
          <div
            class="h-52 md:h-[24rem] rounded-t-xl relative group"
            :style="{
              backgroundImage: 'url(' + project.Image + ')',
              backgroundSize: 'cover',
              backgroundPosition: 'center',
              backgroundRepeat: 'no-repeat',
            }"
          ></div>
          <div
            class="overlay items-center justify-center absolute top-0 left-0 w-full h-full bg-[#181818] bg-opacity-0 hidden group-hover:flex group-hover:bg-opacity-80 transition-all duration-500"
          ></div>
          <div
            class="text-white rounded-b-xl mt-3 bg-[#111a3e] shadow-lg border border-[#1f1641] py-6 px-4"
          >
            <h3
              class="text-lg font-semibold uppercase flex justify-center lg:text-xl"
            >
              {{ project.title }}
            </h3>
            <p class="text-[#ADB7BE]">{{ project.description }}</p>
            <div class="flex flex-wrap p-2.5 justify-center">
              <div
                v-for="technolgy in project.technologies"
                :key="technolgy"
                class="text-center ml-1 mt-1 rounded-3xl bg-[#111827]"
                style="
                  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
                  border: 1px solid #111827;
                  backdrop-filter: blur(9px);
                  -webkit-backdrop-filter: blur(9px);
                "
              >
                <p class="px-1 py-2">{{ technolgy }}</p>
              </div>
            </div>
            <a :href="project.webURL" target="_blank">
              <strong
                class="text-gray-200 right-0 text-xs flex justify-center underline"
                >Vist Site</strong
              ></a
            >
          </div>
        </div>
      </ul>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue";

const Projects = ref([
  {
    id: 1,
    category: "web development",
    Image: "https://i.ibb.co/Pv6yCxDH/clean.png",
    title: "CLEANING CO. (RESPONSIVE) ",
    description:
      "Key Features : Fully responsive design for all devices using Vue.js + TailwindCSS - Supports both light and dark modes - Navigation bar with hamburger menu on small screens - Sidebar opens from the side and closes automatically upon section. Smooth scrolling between sections when links are clicked ",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://free-cool.com/",
  },
  {
    id: 2,
    category: "web development",
    Image: "https://i.ibb.co/s9ZNZtC4/Dats.png",
    title: "DATESCO. (RESPONSIVE) ",
    description:
      "key Features : Fully responsive design for all devices using HTML, CSS, and JavaScript - Uses Flexbox and Grid for flexible layout system - Supports both Arabic and English languages - Stores language preference in localStorage - Dual color scheme (dark/light mode) - Hamburger menu for mobile devices - Scroll animations (fade-in, slide-in) - Fixed WhatsApp button for quick communication - Smooth CSS transitions - Card rotation effects -",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/Durar-Dates-Co/",
  },

  {
    id: 3,
    category: "web development",
    Image: "https://i.ibb.co/HLF80fLv/clean2.png",
    title: "CLEANING CO.  (RESPONSIVE)",
    description:
      "Key Features : Fully responsive design for all devices using Vue.js + TailwindCSS  -Supports both light and dark modes  - Navigation bar with hamburger menu on small screens - Sidebar opens from the side and closes automatically upon section selection - Smooth scrolling between sections when links are clicked",
    technologies: ["vue.js 3", "TailwindCss", "vite"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/vue-website/",
  },
  {
    id: 4,
    category: "web development",
    Image: "https://i.ibb.co/XZvXtVW8/dashboard.png",
    title: "DASHBOARD  (RESPONSIVE)",
    description:
      "developed a responsive admin panel with real-time analytics using vue.js, Vite ,Tailwind CSS ",
    technologies: ["vue.js 3", "Tailwind CSS", "Vite"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/Deploy-Dashboard/",
  },
  {
    id: 5,
    category: "web development",
    Image: "https://i.ibb.co/zWMdP27z/login.png",
    title: "LOGIN PAGE  (RESPONSIVE)",
    description: "designed and developed a login page to showcase my skills ",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/Login-Signup/",
  },
  {
    id: 6,
    category: "web development",
    Image: "https://i.ibb.co/vCydLz8Z/travel.png",
    title: "TRAVEL WEBSITE  (RESPONSIVE) ",
    description:
      "designed and developed a Travel website to showcase my skills using HTML, CSS, and JavaScript.",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/Travel/",
  },
  {
    id: 7,
    category: "web development",
    Image: "https://i.ibb.co/PvQkwyL0/profile.png",
    title: "3D PROFILE ",
    description:
      "designed and developed a coffee shop website to showcase my skills using HTML, CSS, and JavaScript.",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/3D-profile/",
  },
  {
    id: 8,
    category: "web development",
    Image: "https://i.ibb.co/xtg9JYNp/elev.png",
    title: "ELEVATOR CO. (RESPONSIVE) ",
    description:
      "Key Features: Fully Responsive Design - Bilingual Support (Arabic/English) - Dynamic Visuals - High Performance - Key Sections - Modern Elements - Easy Customization",
    technologies: ["vue.js 3", "TailwindCss"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/ElevatorCoWebsite/",
  },
  {
    id: 9,
    category: "web development",
    Image: "https://i.ibb.co/tpwThvF6/clean3.jpg",
    title: "House-Cleaning CO. (RESPONSIVE) ",
    description:
      "Modern One-Page Design with dark/light mode toggle, smooth animations (AOS, Swiper), and intuitive circular navigation for seamless user experience. High-Conversion Elements like fixed WhatsApp/call buttons, animated statistics counter, service selection contact form, and fully responsive layout.",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://home-vision.info/",
  },
  {
    id: 10,
    category: "web development",
    Image: "https://i.ibb.co/Mk9WDhfG/hoor.jpg",
    title: "Hoor-Cleaning CO. (RESPONSIVE) ",
    description:
      "Modern One-Page Design with dark/light mode toggle, smooth animations (AOS, Swiper), and intuitive circular navigation for seamless user experience. High-Conversion Elements like fixed WhatsApp/call buttons, animated statistics counter, service selection contact form, and fully responsive layout.",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hoor-clean.org/",
  },
  {
    id: 11,
    category: "web development",
    Image: "https://i.ibb.co/Xkpdp8kc/ecom.jpg",
    title: "Ecommerce. (RESPONSIVE) ",
    description:
      "Modern Design, Lorem ipsum dolor sit amet consectetur, adipisicing elit Lorem ipsum dolor sit amet consectetur, adipisicing elit. Est voluptas aut officiis quam eaque doloribus saepe qui soluta rerum corrupti perferendis ipsum libero,",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/Ecommerce-Website-/",
  },

  {
    id: 12,
    category: "web development",
    Image: "https://i.ibb.co/CDLQqvL/hospital.png",
    title: "Hospital-Website. (RESPONSIVE) ",
    description:
      "Modern Design,smooth animations (AOS, Swiper), Lorem ipsum dolor sit amet consectetur, adipisicing elit Lorem ipsum dolor sit amet consectetur, adipisicing elit. Est voluptas aut officiis quam eaque doloribus saepe qui soluta rerum corrupti perferendis ipsum libero,",
    technologies: ["HTML", "CSS", "JavaScript"],
    gitURL: "",
    webURL: "https://hassan-abd-el-aziz.github.io/Hospital/",
  },
  {
    id: 13,
    category: "mobile App",
    Image: "https://i.ibb.co/RGT2hjB8/mob3.jpg",
    title: "mobile App for...",
    description:
      "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Est voluptas aut officiis quam eaque doloribus saepe qui soluta rerum corrupti perferendis ipsum libero, accusantium consequatur sunt impedit. Repellat, porro rerum!",
    technologies: ["vue.js 3", "vuex", "Express"],
    gitURL: "",
    webURL: "",
  },
  {
    id: 14,
    category: "mobile App",
    Image: "https://i.ibb.co/zHSDkSFZ/mob1.png",
    title: "mobile App for...",
    description:
      "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Est voluptas aut officiis quam eaque doloribus saepe qui soluta rerum corrupti perferendis ipsum libero, accusantium consequatur sunt impedit. Repellat, porro rerum!",
    technologies: ["vue.js 3", "vuex", "Express"],
    gitURL: "",
    webURL: "",
  },
  {
    id: 15,
    category: "mobile App",
    Image: "https://i.ibb.co/GQdyzVkv/mob2.webp",
    title: "mobile App for...",
    description:
      "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Est voluptas aut officiis quam eaque doloribus saepe qui soluta rerum corrupti perferendis ipsum libero, accusantium consequatur sunt impedit. Repellat, porro rerum!",
    technologies: ["vue.js 3", "vuex", "Express"],
    gitURL: "",
    webURL: "",
  },
]);

const SelectedCategory = ref("all");
const filteredProjects = computed(() => {
  if (SelectedCategory.value === "all") {
    return Projects.value;
  }
  return Projects.value.filter(
    (project) =>
      project.category.toLocaleLowerCase() ===
      SelectedCategory.value.toLocaleLowerCase()
  );
});
</script>
