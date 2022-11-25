<template>
  <v-app style="height: 100vh;
  background: radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%);
  overflow: hidden;
  filter: drop-shadow(0 0 10px white);">
    <v-main>
      <Snowfall />
      <router-view />
    </v-main>
    <v-footer class="text-center bg-transparent">
      <v-row justify="center">
        <a href="https://github.com/drblaui/Advent-Door" target="_blank"> Source Code</a>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script setup lang="ts">
import Snowfall from './components/Snowfall.vue';

</script>
<style>
</style>
