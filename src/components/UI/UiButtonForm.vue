<template>
    <div>
        <button class="button__form" @click="clickOnButton">
            <slot></slot>
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
    .button__form {
        background-color: var(--main-text);
        color: var(--title-text);
        padding: 16px 27px;
        border-radius: 42px;
        border: none;
        font-family: 'Lato', sans-serif;
        font-weight: 600;
        font-size: 18px;
        cursor: pointer;
    }

    .button__form:hover {
        background-color: #4f4f4f;
        transition: background-color 0.3s ease;
    }

    .button__form:active {
        background-color: #9a9a9a;
        transition: background-color 0.2s ease;
    }
</style>