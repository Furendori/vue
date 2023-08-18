<script setup>
import { ref, computed } from "vue";
import Counter from "./components/Counter.vue"

let name = ref('')
let age = ref(0)
let ageTenYears = computed(() => {
  return parseInt(age.value) + 10
})

const nameValid = computed(() => name.value.length > 0 && name.value.length <= 15)
const ageValid = computed(() => age.value >= 1 && age.value < 100)

const names = ['Toto', 'Titi', 'Tata', 'Jean', 'Eric', 'Fiorella']
const generate = () => {
  name.value = names[Math.floor(Math.random() * names.length)]
  age.value = Math.floor(Math.random() * 100) + 1
}
</script>

<template>

  <div>
    
    <input type="text" v-model="name" placeholder="Nom">
    <p v-if="name.length > 15">Maximum 15 caractères</p>
    <input type="text" v-model="age" placeholder="Age">
    <p v-if="age > 100">Veuillez entrer un age compris entre 1 et 100</p>

  </div>

  <div v-if="name.length > 1 && age > 0" class="infos">
    <p>Je m'appelle {{ name }} et j'ai {{ age }} ans</p>
    <p>Dans 10 ans, j'aurai {{ ageTenYears }} ans</p>
    <p>Mon nom se compose de {{ name.length }} caractères</p>
    <p>Mon nom est majuscules est {{ name.toUpperCase() }}</p>
  </div>

  <div v-else class="infos-error">
    <p>Veuillez entrer un nom et un age valide</p>
  </div>

  <Counter start = 3></Counter>

</template>

<style scoped>
  .infos {
    background-color: darkgray;
  }

  .infos-error {
    background-color: red;
  }
</style>
