<script setup>
import Computed from "./components/Computed.vue";
import Image from "./components/Image.vue";
import { ref } from "vue";

let isShowing = ref(true);

const count = ref(0);
const increment = (number) => (count.value += number);

let title = "Recettes";
const recettes = ["Couscous", "Fondue", "Salade Cesar", "Tomates cerises"];
</script>

<template>
  <h1>Hello Vue {{ count }}</h1>
  <button @click="increment(1)" v-if="count < 10">Incrémenter</button>
  <button @click="increment(-1)" :disabled="count <= -10">Décrémenter</button>
  <Image source="a042581f4e29026704d" />

  <div class="recette-container">
    <div>
      <h1>{{ title }}</h1>
      <ul v-show="isShowing">
        <li v-for="recette in recettes">{{ recette }}</li>
      </ul>
      <button @click="isShowing = !isShowing">
        Afficher / Cacher la liste
      </button>
    </div>
  </div>
</template>

<style scoped>
.recette-container {
  display: flex;
  flex-direction: column;
  padding: 30px;
}
button {
  background-color: lightblue;
  border: 0;
  cursor: pointer;
}
</style>
