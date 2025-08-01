<template>
    <div>
        <button class="button__plus" @click="clickOnButton">

        </button>
    </div>
</template>

<script setup>
import { PropType } from 'vue';

    const props = defineProps({
        clickOnButton: { type: Function,},
    })
</script>

<style scoped>
    .button__plus {
        width: 55px;
        height: 55px;
        background: linear-gradient(#FFE9B1, #DDA003);
        border: none;
        border-radius: 50px;
        position: relative;
        cursor: pointer;
    }

    .button__plus::after {
        position: absolute;
        content: '+';
        font-family: 'Cabin', sans-serif;
        font-size: 53px;
        font-weight: 600;
        color: #181818;
        left: 0;
        right: 0;
        bottom: 0;
    }

    @media (max-width: 1600px) {
        .button__plus {
        width: 39px;
        height: 39px;
        }

        .button__plus::after {
        font-size: 35px;
        font-weight: 600;
        }
    }

    @media (max-width: 500px) {
        .button__plus {
        width: 30px;
        height: 30px;
        }

        .button__plus::after {
        font-size: 29px;
        font-weight: 600;
        }
    }
</style>