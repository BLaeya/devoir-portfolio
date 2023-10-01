<script setup>
import { reactive, ref } from 'vue'
import data from '../Data/achievements'
import TheModal from '../components/TheModal.vue'

const achievements = reactive(data)

const selectedAchievement = ref(null)
const reveal = ref(false)

function toggleModal(achievement) {
  selectedAchievement.value = achievement
  reveal.value = !reveal.value
}
</script>

<template>
  <h2 class="borderer">Réalisations</h2>
  <ul>
    <li
      v-for="achievement in achievements"
      :key="achievement.id"
      :selectedAchievement="selectedAchievement"
    >
      <h3>{{ achievement.title }}</h3>
      <div
        @click="() => toggleModal(achievement)"
        class="image"
        :style="{ backgroundImage: `url(${achievement.image})` }"
      ></div>
    </li>
  </ul>
  <TheModal :toggleModal="toggleModal" :achievement="selectedAchievement" :reveal="reveal" />
</template>

<style scoped>
.image {
  height: 141px;
  width: 288px;
  background-size: cover;
  margin-left: 10px;
}
</style>
