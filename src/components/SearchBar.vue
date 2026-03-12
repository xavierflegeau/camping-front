<template>
  <div class="search-wrapper">
    <div class="search-container">
      <!-- Dates -->
      <div class="field">
        <label>Dates</label>
        <DatePicker
          v-model="dates"
          selectionMode="range"
          dateFormat="dd/mm/yy"
          placeholder="Choisir les dates"
          showIcon
        />
      </div>

      <!-- Type -->
      <div class="field">
        <label>Type</label>
        <Dropdown v-model="selectedType" :options="types" optionLabel="label" placeholder="Tous" />
      </div>

      <!-- Qui vient -->
      <div class="field">
        <label>Qui vient ?</label>
        <Dropdown v-model="guests" :options="guestOptions" optionLabel="label" />
      </div>

      <!-- Button -->
      <Button label="Rechercher" icon="pi pi-search" class="search-btn" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

import DatePicker from 'primevue/datepicker'
import Dropdown from 'primevue/dropdown'
import Button from 'primevue/button'

const dates = ref()
const selectedType = ref()
const guests = ref()

const types = [{ label: 'Tous' }, { label: 'Emplacement' }, { label: 'Mobil-home' }]

const guestOptions = [
  { label: '1 adulte' },
  { label: '2 adultes' },
  { label: '2 adultes – 1 enfant' },
  { label: '2 adultes – 2 enfants' },
]
</script>

<style scoped>
/* wrapper pour centrer l'encadré */
.search-wrapper {
  display: flex;
  justify-content: center;
  margin: 30px 0; /* espace autour de la barre */
}

/* le container vert transparent */
.search-container {
  display: flex;
  gap: 20px;
  padding: 25px;
  border-radius: 12px;
  background: rgb(255, 255, 255); /* vert transparent */
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1); /* léger ombre pour détacher du fond */
  align-items: flex-end;
  justify-content: center;
  flex-wrap: wrap;
  max-width: 1000px; /* largeur max de l'encadré */
  width: 90%; /* largeur responsive */
}

.field {
  display: flex;
  flex-direction: column;
  gap: 6px;
  min-width: 220px;
}

label {
  font-weight: 600;
}

.search-btn {
  height: 44px;
}

/* Mobile */
@media (max-width: 900px) {
  .search-container {
    flex-direction: column;
    align-items: center;
  }

  .field {
    min-width: 100%;
  }

  .search-btn {
    width: 100%;
  }
}
</style>
