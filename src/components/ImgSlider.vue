<template>
    <div 
        class="container__img"
        @mouseover="isHovered = true"
        @mouseleave="isHovered = false"
    >
        <div class="img-wrapper">
            <img class="img" :src="urlImage" alt="изображение офиса" />
        </div>
        <div 
        v-if="isHovered"
        class="container__img-overlay">
            <UiButtonPlus class="overlay__button" :clickOnButton="clickOnButton"/>
            <h3 class="overlay__title">Taxes & Efficiency</h3>
            <p class="overlay__text">Business</p>
        </div>
    </div>
</template>

<script setup lang="ts">
    import { ref } from 'vue';
import UiButtonPlus from './UI/UiButtonPlus.vue';

    const isHovered = ref(false);

    const props = defineProps({
        urlImage: { type: String, default: 0 },
        clickOnButton:  {type: Function}
    })
</script>

<style scoped>
    .container__img {
        position: relative;
        border-radius: 20px;
        overflow: hidden;
    }

    .img-wrapper {
        position: relative; 
        width: 100%;
        height: 100%;
    }

    .img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: filter 0.3s;
    }

    .img-wrapper:hover .img {
        filter: blur(8px);
    }

    .img-wrapper::after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(rgba(24, 24, 24, 0.75), #181818);
        opacity: 0; 
        transition: opacity 0.3s ease;
        z-index: 1;
    }

    .img-wrapper:hover::after {
        opacity: 1; 
    }

    .container__img-overlay {
        position: absolute;
        content: '';
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 2;
        background: linear-gradient(rgba(24, 24, 24, 0.75), #181818);
        opacity: 0; 
        transition: opacity 0.3s ease;
    }

    .container__img-overlay:hover {
        opacity: 1;
    }

    .overlay__button {
        position: absolute;
        right: 30px;
        top: 30px;
    }

    .overlay__title {
        position: absolute;
        font-family: 'Cobit', sans-serif;
        font-weight: 600;
        font-size: 25px;
        color: var(--title-text);
        left: 25px;
        bottom: 52px;
    }

    .overlay__text {
        position: absolute;
        font-family: 'Lato', sans-serif;
        font-weight: 400;
        font-size: 16px;
        color: var(--accent-color);
        left: 25px;
        bottom: 24px;
    }

    @media (max-width: 1600px) {
        .overlay__button {
            right: 15px;
            top: 15px;
        }

        .overlay__title {
            font-size: 19px;
            left: 15px;
            bottom: 39px;
        }

        .overlay__text {
            font-size: 12px;
            left: 15px;
            bottom: 20px;
        }  
    }

    @media (max-width: 900px) {

        .overlay__title {
            font-size: 15px;
            left: 10px;
            bottom: 39px;
        }

        .overlay__text {
            font-size: 12px;
            left: 10px;
            bottom: 10px;
        }  
    }

    @media (max-width: 500px) {

        .overlay__title {
            font-size: 12px;
            left: 10px;
            bottom: 30px;
        }

        .overlay__text {
            font-size: 10px;
            left: 10px;
            bottom: 10px;
        }  
    }
</style>