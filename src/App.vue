<template>
  <div class="app">
    <Tabs/>
  </div>
</template>

<script setup>
  import Tabs from './components/Tabs.vue';
</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --accent-color: #FFCC4A;
  --title-text: #FFFFFF;
  --main-text: #181818;
  --additional-text: #595566;
  --swiper-theme-color: #FFCC4A;

}

.app {
  width: 100%;
  padding-inline: 18.45%;
}

@media (max-width: 1300px) {
  .app {
    padding-inline: 13%;
  }
}

</style>
