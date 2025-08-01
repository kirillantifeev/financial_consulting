<template>
    <div>
        <button class="button__procces" @click="clickOnButton">
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
    .button__procces {
        background-color: var(--accent-color);
        font-family: 'Lato', sans-serif;
        font-weight: 400;
        font-size: 16px;
        color: var(--main-text);
        text-transform: uppercase;
        border: none;
        border-radius: 20px;
        padding: 1px 15px;
    }
</style>