<script setup>
import Nav from "./components/includes/Nav.vue";
import NavTop from "./components/includes/NavTop.vue";
import {useRoute} from "vue-router";
</script>

<template>
  <NavTop/>
  <Nav/>
  <router-view :key="$route.fullPath"/>
</template>

<style scoped>

</style>
