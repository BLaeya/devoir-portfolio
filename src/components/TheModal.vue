<script setup>
const { achievement, reveal, toggleModal } = defineProps(['achievement', 'reveal', 'toggleModal'])
</script>

<template>
  <div class="container" v-if="reveal">
    <div class="bloc-modale">
      <div class="overlay" @click="toggleModal"></div>
      <div class="modale">
        <button @click="toggleModal">x</button>
        <h3 class="borderer">{{ achievement.title }}</h3>
        <p>Description: {{ achievement.description }}</p>
        <p>Date de création: {{ achievement.creationDate }}</p>
        <p>Date de dernière révision: {{ achievement.revisionDate }}</p>
        <p>Technologie: {{ achievement.techno }}</p>
        <a :href="achievement.pdf" target="_blank">Pdf du site</a>
        <a :href="achievement.url" target="_blank"
          ><div class="image" :style="{ backgroundImage: `url(${achievement.image})` }"></div
        ></a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bloc-modale {
  position: fixed;
  inset: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;
}

.overlay {
  background-color: rgba(73, 84, 90, 0.802);
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 2;
}

.modale {
  background-color: #9db5c0;
  position: fixed;
  color: #253337;
  border: 1px solid #253337;
  border-radius: 10px;
  z-index: 3;
}
.image {
  background-size: cover;
  height: 423px;
  width: 864px;
  border-radius: 10px;
  position: relative;
  top: 10px;
  right: -50px;
}

button {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #fe938c;
  height: 30px;
  width: 30px;
  vertical-align: center;
}
h3 {
  text-align: center;
  padding: 20px 0 40px 0;
  width: 864px;
  margin: auto;
  margin-top: 40px;
}
a {
  color: #253337;
  text-decoration: none;
  padding: 0 50px;
}
p {
  padding: 0 50px;
  width: 864px;
}
.container {
  max-width: 70%;
}
</style>
