<template>
  <div class="h-[500vh] relative">
    <NavBar />
    <ScrollProgress />
    <HeroSection />

    <section id="services" class="relative z-10 min-h-screen pt-20 px-4">
      <div class="max-w-6xl mx-auto">
        <ServiceCard />

      </div>
    </section>

    <section class="relative z-10 min-h-screen pt-20 px-4 bg-black/80">
      <div class="max-w-6xl mx-auto">
        <AboutSection />
      </div>
    </section>
    <section class="relative z-10 min-h-screen pt-5 px-4 bg-gradient-to-r from-[#111a3e] to-[#350958]/80">
      <div class="max-w-6xl mx-auto">
        <ExperienceAndskills />
      </div>
    </section>

    <section class="relative z-10 min-h-screen pt-20 px-4 bg-black/40">
      <div class="max-w-6xl mx-auto">
        <LatestProjSectio />

      </div>
    </section>
<section class="relative z-10 min-h-screen pt-5 px-4 bg-gradient-to-r from-[#111a3e] to-[#350958]/80">
      <div class="max-w-6xl mx-auto">
        <ContactSection />
          <TestimonialsSection/>
      </div>
    </section>

    <footer class="relative z-10 bg-black/80 text-white mt-1 py-5 px-4">
      <div class="max-w-6xl mx-auto text-center">
        <p>&copy; 2026 Portfolio Website. All rights reserved.</p>
      </div>
    </footer>


    <BackToTop />

  </div>
</template>

<script setup>
import HeroSection from './components/HeroSection.vue';
import ScrollProgress from './components/ScrollProgress.vue';
import ServiceCard from './components/ServicesSection.vue';
import ScrollSection from './components/ScrollSection.vue';
import NavBar from './components/NavBar.vue';
import AboutSection from './components/AboutSection.vue';
import BackToTop from './components/BackToTop.vue';
import ExperienceAndskills from './components/ExperienceAndskills.vue';
import LatestProjSectio from './components/LatestProjSectio.vue';
import ContactSection from './components/ContactSection.vue';
import TestimonialsSection from './components/TestimonialsSection.vue';
</script>