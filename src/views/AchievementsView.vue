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
      <h3
        @click="() => toggleModal(achievement)"
        class="image"
        :style="{ backgroundImage: `url(${achievement.image})` }"
      >
        {{ achievement.title }}
      </h3>
    </li>
  </ul>
  <TheModal :toggleModal="toggleModal" :achievement="selectedAchievement" :reveal="reveal" />
</template>

<style scoped>
.image {
  height: 282px;
  width: 576px;
  background-size: cover;
  text-align: center;
  color: white;
  -webkit-text-stroke-color: #253337;
  -webkit-text-stroke-width: 2px;
  vertical-align: -webkit-baseline-middle;
}

ul {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-around;
  align-content: space-around;
}
li {
  width: 600px;
}

.image:hover {
  box-shadow: 8px 5px 5px #253337;
}
</style>
