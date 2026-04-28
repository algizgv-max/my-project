<script setup>
// core version + navigation, pagination modules:
import Swiper from 'swiper';
import { Navigation, Pagination } from 'swiper/modules';
// import Swiper and modules styles
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import { onMounted, ref } from 'vue';

const manageCards = ref([
  {
    tittle: 'Membership Organisations',
    subtittle: 'Our membership management software provides full automation of membership renewals and payments',
    imageUrl: '/src/assets/img/manage-1.svg'
  },
  {
    tittle: 'National Associations',
    subtittle: 'Our membership management software provides full automation of membership renewals and payments',
    imageUrl: '/src/assets/img/manage-2.svg'
  },
  {
    tittle: 'Clubs & Groups',
    subtittle: 'Our membership management software provides full automation of membership renewals and payments',
    imageUrl: '/src/assets/img/manage-3.svg'
  }
])

onMounted(hook => {
  const swiper = new Swiper('.manage-swiper', {
    // configure Swiper to use modules
    modules: [Navigation, Pagination],
    slidesPerView: 1,
    spaceBetween: 10,
    breakpoints: {
      576: {
        slidesPerView: 1.5,
        spaceBetween: 24,
      },
      768: {
        slidesPerView: 3,
        spaceBetween: 24,
      },
    },
    // If we need pagination
    pagination: {
      el: '.swiper-pagination',
      clickable: true,
    },

    // Navigation arrows
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev',
    },
  });
})
</script>

<template>
  <section class="manage">
    <div class="container">
      <h2>
        Manage your entire community <br> in a single system
      </h2>
      <p class="manage__subtittle">
        Who is Nextcent suitable for?
      </p>
      <!-- Slider main container -->
      <div class="swiper manage-swiper">
        <!-- Additional required wrapper -->
        <div class="swiper-wrapper">
          <!-- Slides -->
          <div class="swiper-slide" v-for="item in manageCards">
            <div class="manage__card h-100">
              <div class="manage__card-icon">
                <img v-bind:src="item.imageUrl" alt="">
              </div>
              <h4>
                {{ item.tittle }}
              </h4>
              <p>
                {{ item.subtittle }}
              </p>
            </div>
          </div>
        </div>
        <!-- If we need pagination -->
        <div class="swiper-pagination"></div>

        <!-- If we need navigation buttons -->
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
      </div>
    </div>
  </section>
</template>

<style scoped></style>
