<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Header from "./components/Header.vue";
import SportsOverview from "./components/SportsOverview.vue";
</script>

<template>
  <div class="vtmn-bg-background-primary">
    <Header />

    <SportsOverview />
  </div>
</template>

<style>
* {
  font-family: "Roboto", sans-serif;
  font-family: "Roboto Condensed", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 16px;
  box-sizing: border-box;
}

.svg-icon,
.svg-icon * {
  fill: currentColor;
  stroke: none;
}
.svg-icon {
  display: inline-block;
  vertical-align: middle;
  width: 1em;
  height: 1em;
}
</style>
