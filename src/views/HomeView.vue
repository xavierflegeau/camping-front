<script setup lang="ts">
import HeaderComponent from '@/components/HeaderComponent.vue'
import ResultComponent from '@/components/ResultComponent.vue'
import SearchBar from '@/components/SearchBar.vue'

// Aucun code TypeScript nécessaire
</script>

<template>
  <!-- Vidéo en arrière-plan -->
  <video autoplay muted loop class="background-video">
    <source src="/videos/Présentation Camping Golfo di Sogno - 2023.mp4" type="video/mp4" />
    Votre navigateur ne supporte pas la vidéo HTML5.
  </video>

  <!-- Overlay sombre -->
  <div class="overlay">
    <HeaderComponent></HeaderComponent>
    <SearchBar></SearchBar>
    <ResultComponent></ResultComponent>
  </div>
</template>

<style scoped>
/* Reset pour éviter tout scroll et marges */
html,
body {
  margin: 0;
  padding: 0;
  overflow: hidden;
  width: 100%;
  height: 100%;
  font-family: Arial, sans-serif;
}

/* Vidéo plein écran */
.background-video {
  position: fixed;
  top: 50%;
  left: 50%;
  width: 100vw;
  height: 100vh;
  object-fit: cover;
  transform: translate(-50%, -50%);
  z-index: 0;
}

/* Overlay sombre */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  z-index: 1;
  overflow-y: auto;
}
</style>
