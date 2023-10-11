<script setup>
import { ref } from 'vue'

// fonctionnalité affichage message d'erreur
const appear = ref(false)

function error() {
  appear.value = true
}

// fonctionnalité vérification du remplissage des champs
const firstname = ref('')
const lastname = ref('')
const email = ref('')
const message = ref('')

function formEmpty() {
  if (!firstname.value || !lastname.value || !email.value || !message.value) {
    error()
    return true
  }
  return false
}

// fonctionnalité soumettre le formulaire
function submit() {
  if (!formEmpty()) {
    alert('votre email a été envoyé à l.challant@gmail.com')
    appear.value = false
    firstname.value = ''
    lastname.value = ''
    email.value = ''
    message.value = ''
  }
}

// fonstionnalités  pour gérer le focus et le blur
const isFieldFocused = ref(false)

function handleFocus() {
  isFieldFocused.value = true
}
function handleBlur() {
  isFieldFocused.value = false
}
</script>

<template>
  <h2 class="borderer">Contact</h2>
  <div id="contact">
    <p>Pour me contacter, vous pouvez saisir le formulaire suivant.</p>
    <div id="error" v-if="appear">Erreur de saisie du formulaire!</div>
    <form>
      <label for="first-name">Prénom</label>

      <input
        v-model="firstname"
        @focus="handleFocus"
        @blur="handleBlur"
        type="text"
        name="first-name"
        id="first-name"
      />

      <label for="last-name">Nom</label>

      <input
        v-model="lastname"
        @focus="handleFocus"
        @blur="handleBlur"
        type="text"
        name="last-name"
        id="last-name"
      />

      <label for="email">e-mail</label>
      <input
        v-model="email"
        @focus="handleFocus"
        @blur="handleBlur"
        type="email"
        name="email"
        id="email"
      />

      <label for="message">Commentaire</label>
      <span id="message-max">Max. 500 caractères</span>

      <textarea
        v-model="message"
        @focus="handleFocus"
        @blur="handleBlur"
        id="message"
        name="message"
        rows="5"
        maxlength="500"
      ></textarea>

      <button @click.prevent="submit()" type="submit">Envoyer</button>
    </form>
  </div>
</template>

<style scoped>
#contact {
  padding-bottom: 25px;
}
#error {
  background-color: #fe938c;
  color: white;
  height: 50px;
  width: 100%;
  border-radius: 10px;
  text-align: center;
  padding: 25px 0 5px 0;
}
form {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  max-width: 70%;
  margin: auto;
}
button,
input,
textarea {
  border: 1px solid #253337;
  border-radius: 10px;
  margin: 5px;
}
button {
  background-color: #cdeac0;
}
a {
  color: #253337;
  text-decoration: none;
  font-weight: bold;
  padding: 0;
  font-size: 1rem;
}
label,
span {
  font-size: 1rem;
}
p {
  max-width: 70%;
  margin: auto;
  font-size: 1rem;
}
</style>
