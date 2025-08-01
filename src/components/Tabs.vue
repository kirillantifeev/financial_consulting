<template>
    <div class="container__tabs">
        <header class="tabs">
            <div class="block__tabs">
                <button 
                    class="tabs__button"
                    v-for="(tab, index) in tabs"
                    :key="index"
                    @click="activeTab = index"
                    :class="{ active: activeTab === index }"
                >
                    {{ tab.title }}
                </button>
            </div>
        </header>
        <div>
            <div class="component">
                <component :is="tabs[activeTab].component"/>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import TabAll from './tabs/TabAll.vue';
import TabOther from './tabs/TabOther.vue';

const activeTab = ref(0);

const tabs = [
  { title: 'All', component: TabAll },
  { title: 'Taxes & Efficiency', component: TabOther },
  { title: 'Investment banking', component: TabOther },
  { title: 'Financial Plan', component: TabOther },
  { title: 'Audit & Evaluation', component: TabOther },
];
</script>

<style scoped>

    .container__tabs {
        margin-top: 90px;
    }

    .tabs {
        display: flex;
        justify-content: center;
    }

    .block__tabs {
        display: flex;
        gap: 39px;
        padding: 31px 44px;
        background-color: var(--main-text);
        border-radius: 30px;
        margin-bottom: 50px;
    }

    .tabs__button {
        border: none;
        position: relative;
        background-color: var(--main-text);
        color: var(--title-text);
        font-family: 'Cabin', sans-serif;
        font-weight: 600;
        font-size: 1.3vw;
        cursor: pointer;
    }

    .tabs__button::after {
        content: '';
        position: absolute;
        width: 0;
        height: 1.5px;
        bottom: -3px;
        left: 0;
        background-color: var(--title-text);
        transition: width 0.3s ease;
    }

    .tabs__button:hover::after {
        width: 100%;
    }

    .tabs__button.active {
        color: var(--accent-color);
        cursor: auto;
        text-decoration: underline;
        text-underline-offset: 6px;
    }

    .tabs__button.active:hover::after {
        width: 0;
    }

    @media(max-width: 1300px) {

    .container__tabs {
        margin-top: 70px;
    }

    .block__tabs {
        border-radius: 20px;
        margin-bottom: 40px;
        padding: 20px 20px;
    }

    .tabs__button {
        font-size: 1.5vw;
    }   
    }

    @media(max-width: 900px) {

    .container__tabs {
        margin-top: 50px;
    }

    .block__tabs {
        width: 100%;
        flex-direction: column;
        justify-content: center;
        margin-bottom: 40px;
        gap: 26px;

    }

    .tabs__button {
        font-size: 16px;
    }   
    }
</style>