<template>
  <section class="text-white mt-20" id="testimonials" data-aos="zoom-in">
    <h2 class="text-4xl font-bold text-white text-left mb-4 px-4 xl:pl-16">
      Testimonials
    </h2>
    <div class="px-4 xl:px-16">
      <Carousel :breakpoints="breakpoints">
        <slide v-for="element in testimonials" :key="element.id">
          <div class="carousel_item p-4">
            <div
              class="w-full mx-auto bg-[#111a3e] shadow-lg border-[#1f1641] p-5 text-white font-light mb-6"
            >
              <div class="w-full flex mb-4 items-center">
                <div
                  class="overflow-hidden rounded-full w-10 h-10 bg-gray-50 border border-gray-200"
                >
                  <img
                    :src="element.image"
                    alt="testmonial image"
                    loading="lazy"
                  />
                </div>
                <h6 class="ml-4 font-bold text-sm uppercase text-white">
                  {{ element.fullname }}
                </h6>
              </div>
              <div class="w-full">
                <p class="text-sm leading-tight">
                  <span
                    class="text-lg leading-none italic font-bold text-white mr-1"
                    >"</span
                  >
                  {{ element.comment }}
                  <span
                    class="text-lg leading-none italic font-bold text-white mr-1"
                    >"</span
                  >
                </p>
              </div>
            </div>
          </div>
        </slide>
        <template #addons>
          <Navigation />
        </template>
      </Carousel>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import { Carousel, Navigation, Slide } from "vue3-carousel";
import "vue3-carousel/dist/carousel.css";
//Carousel settings
const settingss = ref([
  {
    itemsToShow: 1,
    snapAlign: "center",
  },
]);

//Breakpoints
const breakpoints = ref({
  700: {
    itemsToShow: 2.5,
    snapAlign: "center",
  },
  1024: {
    itemsToShow: 3,
    snapAlign: "start",
  },
});

const testimonials = ref([
  {
    id: 1,
    fullname: "clinet 1",
    image: "https://img.icons8.com/?size=100&id=59743&format=png&color=000000",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur asperiores, nemo amet itaque dicta possimus, maxime est ipsa neque, vero facilis. Ratione nihil laboriosam rem ut eveniet illum, laborum id!.",
  },
  {
    id: 2,
    fullname: "clinet 2",
    image: "https://img.icons8.com/?size=100&id=59743&format=png&color=000000",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur asperiores, nemo amet itaque dicta possimus, maxime est ipsa neque, vero facilis. Ratione nihil laboriosam rem ut eveniet illum, laborum id!.",
  },
  {
    id: 3,
    fullname: "clinet 3",
    image: "https://img.icons8.com/?size=100&id=59743&format=png&color=000000",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur asperiores, nemo amet itaque dicta possimus, maxime est ipsa neque, vero facilis. Ratione nihil laboriosam rem ut eveniet illum, laborum id!.",
  },
  {
    id: 4,
    fullname: "clinet 4",
    image: "https://img.icons8.com/?size=100&id=59743&format=png&color=000000",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur asperiores, nemo amet itaque dicta possimus, maxime est ipsa neque, vero facilis. Ratione nihil laboriosam rem ut eveniet illum, laborum id!.",
  },
  {
    id: 5,
    fullname: "clinet 5",
    image: "https://img.icons8.com/?size=100&id=59743&format=png&color=000000",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur asperiores, nemo amet itaque dicta possimus, maxime est ipsa neque, vero facilis. Ratione nihil laboriosam rem ut eveniet illum, laborum id!.",
  },
  {
    id: 6,
    fullname: "clinet 6",
    image: "https://img.icons8.com/?size=100&id=59743&format=png&color=000000",
    comment:
      "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur asperiores, nemo amet itaque dicta possimus, maxime est ipsa neque, vero facilis. Ratione nihil laboriosam rem ut eveniet illum, laborum id!.",
  },
]);
</script>

<style>
.carousel__prev,
.carousel__next {
  color: white !important;
}
</style>
