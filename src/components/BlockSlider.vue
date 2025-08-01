<template>
    <div v-if="!isActiveSlider" class="container__grid">
        <ImgSlider 
        class="slider__element"
        v-for="elemet in mockImagesSlider" 
        :key="elemet.id" 
        :urlImage="elemet.url"
        :clickOnButton="() => {}" /> 
    </div>

    <div  v-if="isActiveSlider" class="container__slider">
      <swiper
          :modules="[Pagination, Navigation]"
          :pagination="{ clickable: true }"
          :slides-per-view="slidesPerView"
          :navigation="{
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
          }"
          :space-between="20"
        >
          <swiper-slide
            v-for="element in mockImagesSlider" 
            :key="element.id"
            :lazy="true"
          >
            <ImgSlider 
              class="slider__element"
              :urlImage="element.url"
              :clickOnButton="() => {}"
            />
          </swiper-slide>

          <div v-if="slidesPerView === 3" class="swiper-button-prev"></div>
          <div v-if="slidesPerView === 3" class="swiper-button-next"></div>  
      </swiper>
    </div>
    
    
</template>

<script setup lang="ts">
    import { onBeforeUnmount, onMounted, ref } from 'vue';
import ImgSlider from './ImgSlider.vue';
    import { mockImagesSlider } from '@/mockData/mockImagesSlider';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Pagination, Navigation } from 'swiper/modules';
import 'swiper/css';
import "swiper/css/pagination";
import "swiper/css/navigation";

    const isActiveSlider = ref(false);
    const slidesPerView = ref(3)


    const checkScreenSize = () => {
    isActiveSlider.value = window.innerWidth < 800;
    if (window.innerWidth < 680) {
      slidesPerView.value = 2
    }
    if (window.innerWidth < 550) {
      slidesPerView.value = 1
    }
    }

    onMounted(() => {
    checkScreenSize();
    window.addEventListener('resize', checkScreenSize);
    });

    onBeforeUnmount(() => {
    window.removeEventListener('resize', checkScreenSize);
    }); 
      
</script>

<style scoped>
    .container__grid {
        background-color: #F5F5F5;
        padding: 24px 25px;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        border-radius: 30px;
        gap: 25px;
    }

    .container__slider {
      padding: 14px 15px;
      border-radius: 20px;
      background-color: #F5F5F5;
    }

    .slider__element {
        width: 100%;
        aspect-ratio: 1/1;
    }

.swiper-button-prev,
.swiper-button-next {
  color: #000; 
  background: rgba(235, 234, 234, 0.5); 
  width: 30px;
  height: 30px;
  border-radius: 50%;
  transition: opacity 0.3s;
}

.swiper-button-prev::after,
.swiper-button-next::after {
  font-size: 15px; 
}

.swiper-button-prev:hover,
.swiper-button-next:hover {
  opacity: 0.8;
}

.swiper-pagination {
  margin-top: 500px;
}
</style>