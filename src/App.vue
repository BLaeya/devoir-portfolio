<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="container">
    <header>
      <figure>
        <a href="#"><img src="./assets/images/logo-perso-LC.jpg" alt="Logo Laetitia Challant" /></a>
      </figure>

      <h1 class="borderer">Laetitia Challant</h1>

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">A propos</RouterLink>
        <RouterLink to="/achievements">Réalisations</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
        <RouterLink to="/error">Lien cassé</RouterLink>
      </nav>
    </header>

    <main>
      <RouterView />
    </main>

    <footer>
      <div>
        <a href="https://www.linkedin.com/in/laetitia-challant-b73284253/">
          <img src="./assets/images/linkedin.svg" alt="logo linkedin" />
        </a>

        <a href="https://github.com/BLaeya"
          ><img src="./assets/images/square-github.svg" alt="logo gitHub"
        /></a>

        <a href="#"><img src="./assets/images/square-x-twitter.svg" alt="logo twitter" /></a>
      </div>
      <small> Derniere mise à jour le 30/09/2023 à 21h06 <br />Copyright BLaeya 2023 </small>
    </footer>
  </div>
</template>

<style scoped>
main {
  margin: 20px auto;
  width: 70%;
}
.container {
  min-height: 100vh;
  display: grid;
  grid-template-rows: auto 1fr auto;
}
header {
  margin: 0;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-evenly;
  position: sticky;
  top: 0;
  background-color: #9db5c0;
}
h1 {
  height: fit-content;
  font-size: 2rem;
}
nav {
  flex-basis: 100%;
  display: flex;
  justify-content: space-evenly;
}
figure {
  width: 150px;
  height: 150px;
  margin: 10px;
  flex-basis: 1;
}
figure a {
  padding: 0;
}
header img {
  height: 100%;
  width: 100%;
  object-fit: cover;
  border-radius: 50%;
  margin: 0;
}
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #9db5c0;
}

footer img {
  width: 40px;
  height: 40px;
}

small {
  text-align: center;
}
</style>
